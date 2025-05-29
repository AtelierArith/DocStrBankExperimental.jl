```
offset(model::RegressionModel)
```

Return the offset used in the model, i.e. the term added to the linear predictor with known coefficient 1, or `nothing` if the model was not fit with an offset.
