# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
    The purpose of the analysis was to test whether the model could accurately predict an individual's credit-worthiness.

* Explain what financial information the data was on, and what you needed to predict.
    The data included information on current outstanding loans, including the loan size, interest rate, the borrower's income and debt-to-income ratio, the number of open accounts for that borrower, any derogatory marks on the loan (borrower?), and the borrower's total debt. 
    The data also included the loan status for each loan, which was the variable we were trying to predict with the model.

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
    The loan status was a binary data point depicting 0 for healthy loan, and 1 for high-risk loan.

* Describe the stages of the machine learning process you went through as part of this analysis.
    We pulled the loan status out of the dataframe to define it as our prediction variable. We used train_test_split to segment the data into either training, which is fed into the model as the basis of its logic, or testing, which is fed into the model as "new" information to test the efficacy of the model's logic. We then used the LogisticRegression function, with solver 'lbfgs', to train on the training data. When fed the testing data, the confusion_matrix function was able to provide the output which was analysed in the credit_risk_classification.ipynb notebook and below.

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any other algorithms).
    The 'lbfgs' algorithm in the LogisticRegression function is often used for small- to mid-sized data sets. While it's not the only available option, it's known to be a relatively flexible and reliable option.

## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
    * Description of Model 1 Accuracy, Precision, and Recall scores.
    - Precision: the percentage of predicted positives which were positives in the test data
        - Healthy loans: 99%
        - High risk loans: 94%
    - Recall: the percentage of the positives in the test data which were predicted correctly
        - Healthy loans: 100%
        - High risk loans: 84%
    - Accuracy (f1-score): the balanced indicator of both precision and recall
        - Healthy loans: 100%
        - High risk loans: 89%

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:

* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.


I do not recommend using this set of training data as the only input for a model. The available high-risk loan data is dwarfed by the healthy loan data in such a way that the model is skewing toward marking loans healthy which are not. The consumer who takes out a high-risk loan is at greater risk of lowering their own personal financial well-being by defaulting, and the loan provider is also then responsible for actively working to collect the past-due balance.

I also tried running a RandomForestClassifier to help boost the odds of finding the correct outcomes, but the test data didn't include any instances of high-risk loans, which doesn't allow for a good test scenario. 
