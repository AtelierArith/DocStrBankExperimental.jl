```
batched_dot!(o, x, y)
```

インプレースのバッチベクトル-ベクトル乗算で、すべての `k` に対して `o[k] = transpose(x[:,k]) * y[:,k]` に相当します。すべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。
