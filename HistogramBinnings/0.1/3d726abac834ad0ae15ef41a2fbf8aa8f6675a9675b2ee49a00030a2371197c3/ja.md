ヒストグラムのためのエッジベクトルを構築するモジュール。

# 例

```julia
using StatsBase 
using HistogramBinnings

h = fit(Histogram, LogEdgeVector, values)

# またはカスタムエッジベクトルを使用する場合

edges = LogEdgeVector(lo = 1, hi = 1_000_000, nbins = 60)
h = append!(Histogram(edges), values)
```

# エクスポート

このモジュールは以下の型と関数をエクスポートします：

  * `LogEdgeVector`
  * `LinEdgeVector`
  * `midpoints`
