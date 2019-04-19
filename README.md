# 1. Sandtander Customer Transaction Prediction
This respository has my ML solutions for the Santander-Customer-Transaction-Prediction Kaggle's Challenge. A link to the Kaggle site  for this competition can be found [here.](https://www.kaggle.com/c/santander-customer-transaction-prediction). 

# 2. Goal of the Project
Using the dataset provided by Santander in the competition website, the goal was to identify which customers will make a specific transaction in the future, irrespective of the amount of money transacted. The data provided for this competition has the same structure as the real data Santander had available to solve this problem.

# 3. File Descriptions
* *SantanderPrediction.ipynb* the code and explanation of the steps taken
* *train.csv* - the training set
* *test.csv* - the test set. The task in this project is to predict the value of target column for the test set
* *requirements.txt* - a list of packages used for this project
* *train.csv* and *test.csv* can be downloaded from the [competition website.](https://www.kaggle.com/c/santander-customer-transaction-prediction/data)

# 4. Solution Approach
The problem is treated as a binary classification problem as the final goal is to determine whether a customer will make a transaction or not. After importing all the necessary packages for data pre-processing, visualization and modeling, the steps I followed to solve this problem are as below

>*  Feature Inspection
>*  Feature Selection
>*  Train Different Classification Models using Selected Features
>*  Calculate Cross Validation Scores of the Model based on ROC_AUC Metric
>*  Make Predictions Using the Best performing Model
>*  Repeat the Process for top 25,50, 100 and 150 Selected Features  
>*  Perform Hyperparamter Search for Logistic Regression and XGBoost
>*  Submit Solutions of Different Iterations

Detailed explnaton of the steps taken can be found in the *Santander.ipynb* notebook in this repository.

# 4. Summary of Results: 

When modeling was performed with 25 features without doing a hyperparamter search, XGBoost and logisitic Regression were found to be the best performing models in terms of the CV score using the training dataset. Therefore, further iterations with different number of features and hyperparamter optimization was performed using these two models . Below is the table for all iterations and the scores  obtained after making submissions with different iterations. 

 Kaggle LB Score : <br>
                 
| Model |  GridSearch |  No of Selected Features | Kaggle Leaderboard Score|
| --- | --- | --- | --- |
| Logistic Regression|  NO |25|0.753|
| Logistic Regression|  YES |25|0.754|
|  XGBoost|  NO |25|0.786|
|  XGBoost|  NO |50|0.832|
|  XGBoost|  NO |100|0.849|
|  XGBoost|  NO |150|0.849|
  
# 5. Conclusion:

Overall, the prject was a good experience to understand the role of feature selection and hyperparamter optimization in developing accurate machine learning models. 

* The scores show that hyperparamterer tuning using grid search method slightly improved the score for logistic regression. 
* XGBoost with differet numbers of most significant features highlights the importance of feature selection method and how it can help to reduce computational time and prediction accuracy. The score is imporved from 0.786 to 0.832 when number of features included in the model was increased to 50. 
* However, there was a significant increase in the computation time  for iterations with number of features >50 with little to no increase in the accuracy. The scores suggest that the optimum number of features to select is somewhere between 50 and 100, and finding that exact value using univariate selection metihod can be tedious as I will have to iterate the process by selecting  different number of features between 50 and 100.
* It is possible to write a small code or use one of the available packages for a forward selection or recursive elimination apparoach to identify the exact number of features to select. However, as forward selection\recursive elimination are computationally expensive and the accuracy improved only from 0.832 to 0.849  for selecting 100 features instead of 50 features, this option was not explored in this project. 
