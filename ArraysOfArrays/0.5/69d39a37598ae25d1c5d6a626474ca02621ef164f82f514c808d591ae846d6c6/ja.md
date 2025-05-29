```
var(X::AbstractVectorOfSimilarArrays; corrected::Bool = true)
var(X::AbstractVectorOfSimilarArrays, w::StatsBase.AbstractWeights; corrected::Bool = true)
```

`X`の要素ベクトルのサンプル標準偏差を計算します。`X`の要素ベクトルのサンプル分散を計算します。最後の次元に沿った`flatview(X)`の`std`に相当します。
