```
qnorm_boundary(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}(),
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

Returns $L^q$-norm of a function f or its FEM coefficient vector v over the nodes or quadrature points in the boundary elements on the given mesh with q being the conjugated exponent to p.
