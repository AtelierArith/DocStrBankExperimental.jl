```julia
struct Prior{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

因子グラフの変数ノードのすべての次元に対するデフォルトの事前分布。変数に非ユークリッド次元が使用される場合、`Prior`は推奨されません。
