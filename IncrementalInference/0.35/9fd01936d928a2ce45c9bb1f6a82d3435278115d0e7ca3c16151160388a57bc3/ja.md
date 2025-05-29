```julia
mutable struct CliqStateMachineContainer{BTND, G<:DistributedFactorGraphs.AbstractDFG, InMemG<:DistributedFactorGraphs.GraphsDFGs.GraphsDFG, BT<:IncrementalInference.AbstractBayesTree}
```

上向きツリー解決/初期化のためのコンテナ。

DevNotes

  * TODO より直接的なクリークアクセス (cliq, parent, children)、マルチプロセス解決のために
