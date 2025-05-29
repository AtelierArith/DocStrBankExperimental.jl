```
linearindex(g::BipartiteIndexedGraph, v::BipartiteGraphVertex{LR}) where {LR<:LeftorRight}
linearindex(g::BipartiteIndexedGraph, i::Integer, ::Type{LR}) where LR<:LeftorRight
```

Return the linear index of a vertex, specified either by a [`BipartiteGraphVertex`](@ref) or by its index and block.
