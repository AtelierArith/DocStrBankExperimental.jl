```
linearpredictor(model::RegressionModel)
```

Return the model's linear predictor, `Xβ` where `X` is the model matrix and `β` is the vector of coefficients, or `Xβ + offset` if the model was fit with an offset.
