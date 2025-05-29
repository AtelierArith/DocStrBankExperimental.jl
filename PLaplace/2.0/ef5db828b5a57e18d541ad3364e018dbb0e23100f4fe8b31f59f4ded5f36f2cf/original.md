```
compute_normalderivative(
    mesh::Mesh,
    boundary::Set{Boundary},
    v::AbstractVector{Float64};
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, AbstractVector{Float64}}
```

Same as previous `compute_normalderivative(...)`. However takes `Set{Boundary}` of named boundary objects as argument `boundary` and translates it to a `Set{Int64}` containing the indices of the nodes contained in the given boundaries.
