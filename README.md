# CollaborativeFilteringSystem
## Build status:
![Build status](https://travis-ci.org/ycc1107/CollaborativeFilteringSystem.svg?branch=master)

###Instructions

Modeling: We are going to use a technique called collaborative filtering[2]. Collaborative filtering is a method of making automatic predictions (filtering) about the interests of a user by collecting preferences or taste information from many users (collaborating). The underlying assumption of the collaborative filtering approach is that if a person A has the same opinion as a person B on an issue, A is more likely to have B's opinion on a different issue x than to have the opinion on x of a person chosen randomly.

Data preparation: Split the ratingsRDD dataset into three pieces

A training set (RDD), which we will use to train models
A validation set (RDD), which we will use to choose the best model
A test set (RDD), which we will use for our experiments
For example (in python): trainingRDD, validationRDD, testRDD = ratingsRDD.randomSplit([6, 2, 2], seed=0L)
Model training & model selection: Based on the training and validation set, use the Root Mean Square Error (RMSE) [3]to compute the error of each model, then select the best model (hint: The most important parameter to ALS.train() is the rank. You could use a fixed value 0.1 for the regularizationParameter. )

Model evaluation: Apply the best model to the testRDD dataset to decide how good our model is.

Data:

Each line in the ratings dataset (ratings.dat.gz) is formatted as: UserID::MovieID::Rating::Timestamp
Create the ratingsRDD : For each line in the ratings dataset, we create a tuple of (UserID, MovieID, Rating). We drop the timestamp because we do not need it here.