# nosql-challenge


This challenge mainly makes use of Mongo Database, Jupiter Notebook and Panda dataFrames.

In github set up a respository called "nosqlchallenge" and clone it to the folder on personal computer where starter files are stored

Starter files are downloaded on personal computer and extracted inside a folder called "nosqlchallenge". setuo files are as follows: 

  NoSQL_setup_starter.ipynb  

  NoSQL_analysis_starter.ipynb

  establishments.json which is stored in a sub folder called Resources


After the installation of mongo database on personal computer 

In a gitbash shell in file where starter code is stored

 - to start updata mogo database type

   mongosh
    
 - to build datbase "uk_food" type

   use uk_food

 - show current database type
  
   db
 
 - Show current databases in existence type
  
  show dbs

 - Create "establishments" collection which is a table type
 
   db.createCollection("establishments")

 - to show all collections in a database
  
   show collections
 
- In a windows terminal run command 

  mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
  
  This command allows for the installation of 39779 records to be loaded from json file called "establishments.json" into the table "establishments" which is in the     database uk_food which in turn is in the mongo database. The drop part of the comand allows collections to be dropped if they are already present if the database.
  
  Below is proof of installation which appears in the windows terminal where above command was executed

# review the collections in our new database
#(base)
#Olive@DESKTOP-D9INLA1 MINGW64 /d/nosql-challenge/Starter_Code (3)/Starter_Code/Resources
#$ mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
#2023-01-23T23:24:54.500+0000    connected to: mongodb://localhost/
#2023-01-23T23:24:54.506+0000    dropping: uk_food.establishments
#2023-01-23T23:24:57.505+0000    [........................] uk_food.establishments       33.8KB/39.3MB (0.1%)
#2023-01-23T23:24:58.735+0000    [########################] uk_food.establishments       39.3MB/39.3MB (100.0%)
#2023-01-23T23:24:58.736+0000    39779 document(s) imported successfully. 0 document(s) failed to import.
#(base)

#uk_food> db.establishments.countDocuments({})
#39779

Number of records imported was 39779




NoSQL_setup_starter.ipynb was opened in jupyter notebook

These are all the libraries which are necessarty to run the code in file NoSQL_setup_starter.ipynb

# mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
# Import dependencies
from pymongo import MongoClient
import json
import requests 
from pprint import pprint
from sqlalchemy import create_engine, Column, Integer, String, ForeignKey, Float
from sqlalchemy.ext.declarative import declarative_base
Base = declarative_base()


An instance of the MongoClient was created Which is the tool used to speak to the MongoDatabase using port number 27017
Code
mongo = MongoClient(port=27017)

The database uk_food was searched for and then assigned to a variable

Code
# confirm that our new database was created
print(mongo.list_database_names())

output ['admin', 'autosaurus', 'config', 'local', 'met', 'test', 'uk_food']

Find the collections "establishment" in uk_food database

Code
# review the collections in our new database
print(db.list_collection_names())

Output ['establishments']

The database was queried by making searches for particular records,and updated by adding and deleting records, and making changes to records.


NoSQL_analysis_starter.ipynb was opened in jupyter notebook and all the details above pertaining to NoSQL_setup_starter.ipynb was repeated.
In this file the database is interigated for information and the final resluts output in a Pandas dataframe 




