```
crossmodelmatrix(model::RegressionModel)
```

Return `X'X` where `X` is the model matrix of `model`. This function will return a pre-computed matrix stored in `model` if possible.
