```
predict(b::Booster, data; margin=false, training=false, ntree_limit=0)
```

モデル `b` を使用して `data` に対して予測を実行します。これにより、トレーニングまたはテストのターゲットデータと比較できる `Vector{Float32}` が返されます。

`ntree_limit > 0` の場合、最初の `ntree_limit` 本の木のみが予測に使用されます。

## 例

```julia
(X, y) = (randn(100,3), randn(100))
b = xgboost((X, y), 10)

ŷ = predict(b, X)
```
