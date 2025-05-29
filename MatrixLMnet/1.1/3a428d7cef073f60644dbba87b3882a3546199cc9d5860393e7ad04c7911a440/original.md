```
mlmnet_bic_summary(MLMNet_bic::Mlmnet_bic)
```

Summarizes results of BIC-validation by returning a table with: 

  * Lambdas used
  * MSE across folds for each lambda
  * Proportion of zero interaction coefficients across each pair  of lambda and alpha

# Arguments

  * MLMNet*bic = Mlmnet*bic object

# Value

DataFrame summarizing BIC, MSE, proportion of zero interactions across each pair  of lambda and alpha. 
