# Credit Risk Analysis

## OVERVIEW OF THE ANALYSIS

### Purpose

The purpose of the analysis is to compare several machine learning models in predicting credit risk using the credit card dataset from LendingClub, a peer-to-peer lending services company. 

After encoding the data and splitting the dataset into its testing and training groups, it is evident that our dataset, specifically the distribution of our target values, is unbalanced. 

![unbalanced](/Resources/unbalanced.png)

To counteract the imbalance, we performed the following algorithms/models on the data. We evaluated their performance in the hopes of providing LendingClub with a written recommendation on which model to select. 

To evaluate performance, we focused on the following indicators:

1. Balanced accuracy score
2. Precision score
3. Recall score


## RESULTS

### Resampling Models

For the first part of our analysis, we resampled our data using three different algorithms. We then used the resampled data to train a logistic regression model to predict low risk/high risk. 

#### Naive Random Oversampling
![random_over](/Resources/random_over.png)

*Balanced accuracy score = **0.649***
- accuracy above 50%, which is a sign that this model can correctly predict credit risk to a good extent

*Precision for high_risk = **0.01***
- inferior precision
- if the model predicted a person as "high risk," there is a 1% chance that the person is indeed high risk

*Precision for low_risk = **1.00***
- very high precision
- if the model predicted a person as "low risk," there is a 100% chance that the person is indeed low risk 

*Recall for high_risk = **0.62***
*Recall for low_risk = **0.68***
- reasonable and almost equal recall scores for both high_ and low_risk


#### SMOTE Oversampling
![smote](/Resources/smote.png)

*Balanced accuracy score = **0.644***
- accuracy above 50%, which is a sign that this model can correctly predict credit risk to a good extent

*Precision for high_risk = **0.01***
- inferior precision

*Precision for low_risk = **1.00***
- very high precision

*Recall for high_risk = **0.63***

*Recall for low_risk = **0.66***
- reasonable and almost equal recall scores for both high_ and low_risk


#### Undersampling with Cluster Centroids algorithm
![undersampling](/Resources/undersampling.png)

*Balanced accuracy score = **0.596***
- accuracy above 50%, which is a sign that this model can correctly predict credit risk half of the time

*Precision for high_risk = **0.01***
- inferior precision

*Precision for low_risk = **1.00***
- very high precision

*Recall for high_risk = **0.62***
*Recall for low_risk = **0.57***
- reasonable scores for both high_ and low_risk


### Combination Sampling

For the second part of our analysis, we tested a combination of over-and under-sampling with the SMOTEENN algorithm. We then used the resampled data to train a logistic regression model to predict low risk/high risk. 

#### SMOTEENN algorithm 
![combination](/Resources/combination.png)

*Balanced accuracy score = **0.638***
- accuracy above 60%, which is a sign that this model can correctly predict credit risk to a good extent

*Precision for high_risk = **0.01***
- inferior precision

*Precision for low_risk = **1.00***
- very high precision

*Recall for high_risk = **0.71***
- great recall score for high_risk
- the model accurately predicts high-risk individuals as "high risk" 71% of the time 

*Recall for low_risk = **0.56***
- reasonable score low_risk, however still on the low-end


### Ensemble Algorithms

For the third part of our analysis, we tested two ensemble algorithms. We then used the resampled data to train a logistic regression model to predict low risk/high risk. 

#### Balanced Random Forest Classifier
![random_forest](/Resources/random_forest.png)

*Balanced accuracy score = **0.672***
- accuracy above 60%, which is a sign that this model can correctly predict credit risk to a good extent
- not a drastic increase from resampling algorithms

*Precision for high_risk = **0.73***
- superior precision score in comparison to resampling algorithms

*Precision for low_risk = **1.00***
- very high precision

*Recall for high_risk = **0.34***
- poor recall score
- the model accurately predicts high-risk individuals as "high risk" 34% of the time 

*Recall for low_risk = **1.00***
- very high low_risk score
- the model is better at accurately predicting low-risk individuals as "low risk" in comparison to high-risk individuals


#### Easy Ensemble AdaBoost Classifier
![easy_ensemble](/Resources/easy_ensemble.png)

*Balanced accuracy score = **0.925***
- best accuracy score out of all algorithms 

*Precision for high_risk = **0.07***
- inferior precision score

*Precision for low_risk = **1.00***
- very high precision score

*Recall for high_risk = **0.91***
*Recall for low_risk = **1.00***
- superior recall scores for both high_ and low_risk  
- the highest average recall score out of all algorithms


## SUMMARY

### Summary of results:

For this dataset, undersampling method performed the worse, as evident by its very low accuracy score and recall scores that were on the lower end of the spectrum.
All resampling methods had almost the same effect -- all accuracy and recall scores were around 0.60. The most drastic effect on these scores came from the ensemble learning algorithms. 

### Recommendation: 

We recommend the Easy Ensemble AdaBoost Classifier. It had the best balanced accuracy score out of all models, and it also produced the highest recall scores out of all models. 
