```
linearindex(g::BipartiteIndexedGraph, v::BipartiteGraphVertex{LR}) where {LR<:LeftorRight}
linearindex(g::BipartiteIndexedGraph, i::Integer, ::Type{LR}) where LR<:LeftorRight
```

頂点の線形インデックスを返します。これは、[`BipartiteGraphVertex`](@ref) またはそのインデックスとブロックによって指定されます。
