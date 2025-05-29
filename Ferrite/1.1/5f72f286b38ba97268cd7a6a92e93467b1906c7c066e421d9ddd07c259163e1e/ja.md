```
collect_periodic_facets!(facet_map::Vector{PeriodicFacetPair}, grid::Grid, mset, iset, transform::Union{Function,Nothing}; tol=1e-12)
```

[`collect_periodic_facets`](@ref) と同様ですが、すべての一致を既存の `facet_map` に追加します。
