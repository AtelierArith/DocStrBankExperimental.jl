```
nobs(model::BetaRegressionModel)
```

Return the effective number of observations used to fit the model. For weighted models, this is the number of nonzero weights, otherwise it's the number of elements of the response (or equivalently, the number of rows in the model matrix).
