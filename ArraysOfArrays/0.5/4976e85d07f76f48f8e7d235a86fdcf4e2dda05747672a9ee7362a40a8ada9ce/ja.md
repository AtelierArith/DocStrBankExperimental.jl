```
mean(X::AbstractVectorOfSimilarArrays)
mean(X::AbstractVectorOfSimilarArrays, w::StatsBase.AbstractWeights)
```

`X`の要素ベクトルの平均を計算します。これは、最後の次元に沿った`flatview(X)`の`mean`に相当します。
