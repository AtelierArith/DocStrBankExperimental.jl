```
test(mlp::Chain, data::Array{<:AbstractFloat,2}, ntest)
```

ドロップアウト層をオンにして、訓練された `mlp` をテストデータに `ntest` 回適用することで確率的な推定値を返します。

```
test(mlp::Chain, data::Array{<:AbstractFloat,2})
```

ドロップアウト層をオフにして決定論的な推定値を取得します。
