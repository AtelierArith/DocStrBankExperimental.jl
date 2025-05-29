```
predict_with_background(m, X, X_b, α=1) -> Vector{Float64}
```

Predict the class prevalences in the observed data set `X` with the fitted method `m`, taking into account a background measurement `X_b` that is scaled by `α`.
