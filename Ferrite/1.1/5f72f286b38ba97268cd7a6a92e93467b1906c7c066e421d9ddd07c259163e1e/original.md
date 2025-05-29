```
collect_periodic_facets!(facet_map::Vector{PeriodicFacetPair}, grid::Grid, mset, iset, transform::Union{Function,Nothing}; tol=1e-12)
```

Same as [`collect_periodic_facets`](@ref) but adds all matches to the existing `facet_map`.
