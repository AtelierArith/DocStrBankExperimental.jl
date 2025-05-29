```
predict(MLMNet::Mlmnet, newPredictors::Predictors=MLMNet.data.predictors)
```

Calculate new predictions based on Mlmnet object

# Arguments

  * MLMNet = Mlmnet object
  * newPredictors = Predictors object. Defaults to the data.predictors field  in the MLM object used to fit the model.

# Value

4d array of predicted values
