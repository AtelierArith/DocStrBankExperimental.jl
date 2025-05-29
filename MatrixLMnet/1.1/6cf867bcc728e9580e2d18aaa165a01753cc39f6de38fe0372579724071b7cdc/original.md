```
predict(MLMNet::Mlmnet, lambda::Float64, alpha::Float64,
             newPredictors::Predictors=MLMNet.data.predictors)
```

Calculate new predictions based on Mlmnet object and given a lambda 

# Arguments

  * MLMNet = Mlmnet object
  * lambda = lambda penalty to use, a floating scalar
  * alpha = alpha penalty to determine the mix of penalties between L1 and L2 a floating scalar
  * newPredictors = Predictors object. Defaults to the data.predictors field  in the MLM object used to fit the model.

# Value

2d array of predicted values
