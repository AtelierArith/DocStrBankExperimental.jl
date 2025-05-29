```
LinEdgeVector{T}(; lo = 1, hi = 10, nbins::Integer) where T <: Real
```

型 `T` の線形間隔エッジベクトルを構築します。エッジは線形空間で均等に間隔を置かれています。`lo` と `hi` はヒストグラムの下限と上限です。`nbins` はビンの数です。

# 例

```julia
using HistogramBinnings

edges = LinEdgeVector(lo = 1, hi = 1_000_000, nbins = 60)
```
