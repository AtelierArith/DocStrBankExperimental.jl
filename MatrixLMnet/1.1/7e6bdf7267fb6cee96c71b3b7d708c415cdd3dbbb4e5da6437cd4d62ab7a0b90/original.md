```
mlmnet_cv_summary(MLMNet_cv::Mlmnet_cv)
```

Summarizes results of cross-validation by returning a table with: 

  * Lambdas used
  * Average MSE across folds for each lambda
  * Average proportion of zero interaction coefficeints across folds for each  lambda

# Arguments

  * MLMNet*cv = MLMNet*cv object

# Value

DataFrame summarizing average MSE and proportion of zero interactions across  folds for each lambda. 
