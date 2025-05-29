```
confint(cb::PlugInConfidenceBand, θ::AbstractVector, Σ::AbstractMatrix; level::Real=0.9)
```

指定されたプラグイン信頼帯を、点推定 `θ` と分散共分散行列 `Σ` を使用して、信頼レベル `level` で計算します。
