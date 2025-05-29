```julia
unknowns(
    edge::VoronoiFVM.AbstractEdge,
    u::AbstractArray{Tv, 1},
    i
) -> VoronoiFVM.VectorUnknowns

```

Construct vector unknowns on edge.
