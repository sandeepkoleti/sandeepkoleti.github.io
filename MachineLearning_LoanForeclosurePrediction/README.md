Loan Prediction
-----------------------

This project predicts whether the loans acquired by Fannie Mae will go into foreclosure.  
Fannie Mae acquires loans from other lenders as a way of inducing them to lend more.
Fannie Mae releases data on the loans it has acquired and their performance afterwards.
I downloaded data from (http://www.fanniemae.com/portal/funding-the-market/data/loan-performance-data.html).

Fannie Mae requires us to register in terms of downloading the data. It does not authorize free sharing of data.
So I am not loading data to the data folder in this project.
I downloaded data for 8 quarters of 2012 and 2013. The data is of large size 20GB.

The data directory contains the downloaded files in txt format
The processed directory contains the files created by python

Assembly.py:
This program combines the acquisition files for all the 8 quarters into 1 file
It also combines the performance files for all the 8 quarters into 1 file
The output files are stored in the processed directory

Annotate.py
This program contains the core business logic.
Bascially, I am  looking for the loans with foreclosure date. If there is no foreclosure date, then the loan has never been to foreclosures. This is added to the status variable
I am adding each account and the count of foreclosure dates into a dictionary
To save memory, I used a dictionary and iterator. If not, I can directly use apply or groupby function to the data
Given that this a dictionary, now I can pass the loan account as key and get the status as the value
There are many categorical values in the dataset. So I am creating updating the column as a categorical column by using astype method and finding .cat.codes
I am converting other relevant fields to numeric values
I am filling null values
Finally, I am adding all the data to train.csv in processed folder.

Predict.py
THis program uses logistic regression machine learning model. Given that our problem is binary classification, logistic regression is better. It runs very fast and uses little memory
Random forests would create dozens of trees
Support vector machine would perform expensive transformations
Logistic regression would perform far fewer stps involving fewer matrix operations
It contains three fucntions to compute error, compute false negatives and false positives
This runs cross validation across the training set and prints the accuracy score


My final project directory looks like this in my computer:

Data
	Acquisition_2012Q1.txt
	Acquisition_2012Q2.txt
	Acquisition_2012Q3.txt
	Acquisition_2012Q4.txt
	Performance_2012Q1.txt
	Performance_2012Q2.txt
	Performance_2012Q3.txt
	Performance_2012Q4.txt

Processed
	Acquisition.txt
	Performance.txt
	train.csv
	
.gitignore
annotate.py
assemble.py
predict.py
README.md
requirements.txt
settings.py
	

