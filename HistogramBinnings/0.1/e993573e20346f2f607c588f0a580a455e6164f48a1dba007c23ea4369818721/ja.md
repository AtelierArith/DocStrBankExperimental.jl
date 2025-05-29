```
LogEdgeVector{T}(; lo = 1, hi = 10, nbins::Integer) where T <: Real
```

型 `T` の対数的に間隔を空けたエッジベクターを構築します。エッジは対数空間で均等に間隔を空けられています。`lo` と `hi` はヒストグラムの下限と上限です。`nbins` はビンの数です。

# 例

```julia
using HistogramBinnings

edges = LogEdgeVector(lo = 1, hi = 1_000_000, nbins = 60)
```
