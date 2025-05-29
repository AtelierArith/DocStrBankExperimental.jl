```julia
isPathFactorsHomogeneous(dfg, from, to)

```

因子グラフ内の2つのノード間の型のベクトルを持つ(::Bool,::Vector{TypeName})を返します

開発ノート

  * 現在のところ、LigthDFGでのみ動作します。

関連

[`GraphsDFG.findShortestPathDijkstra`](@ref)
