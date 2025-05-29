```
inneighbors(g::BipartiteIndexedGraph, v::BipartiteGraphVertex{<:LeftorRight})
```

変数 `v` の隣接点への遅延イテレータを返します。`v` は [`BipartiteGraphVertex`](@ref) によって指定されます。
