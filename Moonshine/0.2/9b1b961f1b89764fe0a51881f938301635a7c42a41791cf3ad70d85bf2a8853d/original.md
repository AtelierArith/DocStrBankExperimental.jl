```
nlive!(counts, genealogy, lats, ωs[, stack]; block_predicates = [], buffer = default_buffer())
```

Number of live edges in a (marginal) genealogy at a given latitude.

Counts are stored in `counts` which is filled with 0s initially. ̀`lats` must be the same size as `counts`.

`block_predicate` and `stack` are passed directly to [`edges_interval`](@ref).

See also [`nlive`](@ref).

# Methods

```julia
nlive!(
    counts,
    genealogy,
    lats,
    ωs,
    stack;
    block_predicates,
    buffer
)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:1163`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
nlive!(
    counts,
    genealogy,
    lats,
    ωs;
    block_predicates,
    buffer
)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:1192`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).
