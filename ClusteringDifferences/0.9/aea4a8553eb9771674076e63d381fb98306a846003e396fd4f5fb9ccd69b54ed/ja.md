```
kmeans(X::AbstractMatrix{<:Real}, r::AbstractVector{Int},
    c::AbstractVector{Int}, μ::AbstractMatrix{<:Real}; <keyword arguments>)
```

データ `X` を $k$-平均アルゴリズムでクラスタリングします。

# キーワード引数

  * `maxiter::Int=256`: 最大反復回数。
  * `dist::SemiMetric=SqEuclidean()`: 距離関数。
  * `ϵ::AbstractFloat=1.0e-6`: 収束のための絶対許容誤差。
