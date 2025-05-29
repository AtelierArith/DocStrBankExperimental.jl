```julia
struct MsgPrior{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

因子グラフの変数ノードのすべての次元におけるメッセージプライオリティ。

ノート

  * CSM操作中のみ一時的に存在します。
