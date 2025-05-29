```
predict(b::Booster, data; margin=false, training=false, ntree_limit=0)
```

Use the model `b` to run predictions on `data`.  This will return a `Vector{Float32}` which can be compared to training or test target data.

If `ntree_limit > 0` only the first `ntree_limit` trees will be used in prediction.

## Examples

```julia
(X, y) = (randn(100,3), randn(100))
b = xgboost((X, y), 10)

ŷ = predict(b, X)
```
