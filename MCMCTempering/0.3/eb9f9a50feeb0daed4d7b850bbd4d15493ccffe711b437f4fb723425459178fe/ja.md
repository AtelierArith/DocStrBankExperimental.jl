```
make_tempered_model([sampler, ]model, beta)
```

`beta` で温度調整された `model` を表すインスタンスを返します。

返り値の型は [`compute_logdensities`](@ref) での使用に依存します。
