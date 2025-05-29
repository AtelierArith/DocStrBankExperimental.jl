```
update(filter::AbstractFilter, b0::GaussianBelief, u::AbstractVector,
    y::AbstractVector)
```

AbstractFilter フィルターを使用して、制御ベクトル u と測定ベクトル y が与えられたときにガウス信念 b0 を更新します。
