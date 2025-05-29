```
index = ParetoSet(X[, sense])
```

与えられた観測値 `X` からパレート集合を取得します。

# 引数

  * `X::AbstractMatrix{Real}` size(X)=(n*objectives, n*samples)
  * `sense::AbstractVector{Union{Symbol, EGOSense}}=repeat(:Min, n_objectives)` 各目的の感覚、size(S)=(n_objectives,)
