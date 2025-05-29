```
vertex(g::BipartiteIndexedGraph, i::Integer)
```

Build the [`BipartiteGraphVertex`](@ref) corresponding to linear index `i`. Throws an error if `i` is not in the range of vertices of `g`
