```
qnorm(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

Returns $L^q$-norm of a FEM coefficient vector v over the nodes or quadrature points in the elements on the given mesh with q being the conjugated exponent to p.
