```
get_strongly_connected_components(h::H) where {H <: AbstractDirectedHypergraph}
```

Return an array of strongly connected components in the directed hypergraph `h` (array of vectors of vertices), based on the "naive" algorithm of Francisco José Martín-Recuerda Moyano (PhD dissertation, 2016).
