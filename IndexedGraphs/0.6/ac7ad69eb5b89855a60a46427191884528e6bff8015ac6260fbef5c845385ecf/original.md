```
outedges(g::BipartiteIndexedGraph, v::BipartiteGraphVertex{<:LeftorRight})
```

Return a lazy iterator to the edges incident on a variable `v` specified by a [`BipartiteGraphVertex`](@ref), with `v` as the source. 
