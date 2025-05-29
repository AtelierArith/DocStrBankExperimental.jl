```
compute_normalderivative(
    mesh::Mesh,
    boundary::Set{Boundary},
    v::AbstractVector{Float64};
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, AbstractVector{Float64}}
```

Returns normal derivative of a function on all or specified boundary elements of the mesh. Each key r represents the derivative of the component r in outer normal direction.
