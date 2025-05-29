```
predict(model::RegressionModel, [newX])
```

Form the predicted response of `model`. An object with new covariate values `newX` can be supplied, which should have the same type and structure as that used to fit `model`; e.g. for a GLM it would generally be a `DataFrame` with the same variable names as the original predictors.
