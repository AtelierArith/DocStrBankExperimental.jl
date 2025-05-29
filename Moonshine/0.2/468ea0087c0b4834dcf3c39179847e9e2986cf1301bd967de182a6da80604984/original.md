```julia
nlive(genealogy, lat, ωs; block_predicates, buffer)

```

Number of live edges in a (marginal) genealogy at a given latitude.

`block_predicate` is passed directly to [`edges_interval`](@ref).

See also [`nlive!`](@ref).
