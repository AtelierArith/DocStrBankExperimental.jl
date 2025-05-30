```
edges_interval(genealogy, ωs)
edges_interval(genealogy, ωs, buffer, visited, root = mrca(genealogy), min_latitude = zero(Float64), block_predicates = [])
```

Iterage over a genealogy's edges via [`EdgesInterval`](@ref).

`buffer` can be either a `CheapStack` or an `UnsafeArray` that will be used as buffer for a newly constructed `CheapStack`.

# Methods

```julia
edges_interval(
    genealogy,
    ωs,
    buffer,
    visited,
    root,
    min_latitude;
    block_predicates
)
edges_interval(genealogy, ωs, buffer, visited, root; ...)
edges_interval(genealogy, ωs, buffer, visited; ...)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:1092`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
edges_interval(genealogy, ωs)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:1097`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
