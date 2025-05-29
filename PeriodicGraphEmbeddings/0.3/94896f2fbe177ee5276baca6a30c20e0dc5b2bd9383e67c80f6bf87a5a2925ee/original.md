```
PeriodicGraphEmbedding{D,T}(pge::PeriodicGraphEmbedding{N,S}) where {D,T,N,S}
PeriodicGraphEmbedding{D}(pge::PeriodicGraphEmbedding{N,S}) where {D,N,S}
```

Return a [`PeriodicGraphEmbedding{D,T}`](@ref) with the same structural information as the input `pge` but embedded in `D` dimensions instead of `N`.

If `T` is not provided it defaults to `S`.

The same caveats that apply to `PeriodicGraph{D}(graph::PeriodicGraph{N})` are valid here: namely, the dimensionality of the graph should be at least `D` and the behaviour is undefined if `D < N` and there are multiple non-identical connected components.

Moreover, if `D < N`, the `N-D` last coordinates of all vertices must be zero or this function will error.
