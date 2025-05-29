```
inedges(g::BipartiteIndexedGraph, v::BipartiteGraphVertex{<:LeftorRight})
```

変数 `v` に指定された [`BipartiteGraphVertex`](@ref) に接続されたエッジへの遅延イテレータを返します。`v` は宛先です。
