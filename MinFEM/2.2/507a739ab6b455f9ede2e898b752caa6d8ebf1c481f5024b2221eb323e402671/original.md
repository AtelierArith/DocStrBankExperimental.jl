```
pnorm_boundary(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}(),
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

Returns $L^p$-norm of a FEM coefficient vector v over the nodes or quadrature points  in the boundary elements on the given mesh. Note that for p=Inf, the values do not get inter- or extrapolated and thus it might not be true maximum over the domain, but only over the given data.
