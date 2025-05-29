```
result_type(dist::PreMetric, Ta::Type, Tb::Type) -> T
result_type(dist::PreMetric, a::AbstractArray, b::AbstractArray) -> T
```

メトリック `dist` の入力タイプ `Ta` と `Tb`、または入力データ `a` と `b` に基づいて結果の型を推論します。
