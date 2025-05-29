```
get_weakly_connected_components(h::H) where {H <: AbstractDirectedHypergraph}
```

Return an array of weakly connected components in the directed hypergraph `h` (array of vectors of vertices) by first converting the directed hypergraph into an undirected hypergraph and then obtaining the conected components of that hypergraph.
