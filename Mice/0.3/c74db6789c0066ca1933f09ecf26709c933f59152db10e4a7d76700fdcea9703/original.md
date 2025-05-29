```
makePredictorMatrix(data)
```

Returns an AxisMatrix of integers defining the predictors for each variable in `data`. The variables to be predicted are on the rows, and the predictors are on the columns. The default is to use all variables as predictors for all other variables (i.e. all 1s except for the diagonal, which is 0).
