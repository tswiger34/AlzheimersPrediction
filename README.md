# Alzheimers Prediction Project
## Overview
In this project, I worked with a class mate to explore the use of advanced deep learning and machine learning techniques to predict Alzheimer's Disease using a dataset of over 2,100 medical images (~60GB) from 492 patients, along with four commonly used biommarkers.

This repository will only include the code that I wrote and reflect my contributions. This will include the data cleaning/EDA along with the deep learning model training, testing, and selection. The deep learning portion took a unique approach to analyzing MRIs by using logistic regression to combine predictions of standard images and the results of image differences.

## Data Cleaning and EDA
The data cleaning/EDA notebook is where all of the data prep was done for both th image data and biomarker data. This included outlier detection, cleaning missing values, getting rid of unnecessary features, and splitting patients into a biomarker training set, image training set, and a test set to be shared for both methods.

Our inclusion criteria can be found in our technical write up, but some important criteria includes no follow up loss for image data, patients in the test set must have both image results and biomarker results, images must go through GradWarp standardization, and where multiple image corrections exist for the same patient/visit combination we only want the image most corrected image (either B1, B2, or B1 and B2 corrected). We also break patients into subgroups that describe their diagnosis path, i.e. cognitively normal at screening, and diagnosed with alzheimer's at a future follow up.

There is a sub-section called "Original Train-Test Split Do Not Run For Reproducibility". The original hypothesis we wanted to test was whether or not a bayesian-hierarchical model could be used to combine biomarkers and imaging results into a final prediction and in this section we found there were not enough patients with both imaging and biomarker results for this to be feasible. For reproducibility purposes, we do not recommend running this section.

The sub section titled "Final Train/Test Split" is what was used to split the data into the training and testing groups used in our final analysis. We also check to make sure the positive/negative class distributions are similar between the image and biomarker sets so we can draw comparisons between the methods as part of our analysis. 

## Deep Learning
The notebook for the deep learning model training and evaluation is titled "ImageClassifiers". This includes the necessary image preprocessing, the creation of simple CNN models, and finetuning of more complex deep learning models. The orignal image training set was split 40/60 with the larger set of patients used to train the image classifiers and the smaller set used for fitting the logistic regression model. The test set was kept in tact with the exception of only including the 
