```
var(X::AbstractVectorOfSimilarArrays; corrected::Bool = true)
var(X::AbstractVectorOfSimilarArrays, w::StatsBase.AbstractWeights; corrected::Bool = true)
```

`X`の要素ベクトルの標本分散を計算します。`flatview(X)`の最終次元に沿った`var`に相当します。
