```
KillAfter(F::Function, args...; timeout::Real=5, verbose::Bool=false, kwargs...)
```

指定された関数 `F` を、設定された `timeout` 制限に達する前に評価しようとし、必要に応じて評価を中断し、`nothing` を返します。注意: 指定された関数は F(args...; kwargs...) を介して評価されます。
