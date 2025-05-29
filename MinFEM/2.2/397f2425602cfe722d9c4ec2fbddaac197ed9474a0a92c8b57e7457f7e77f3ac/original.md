```
pnorm(
    p::Float64,
    v::AbstractVector{Float64},
    mesh::Mesh; 
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Float64
```

Returns $L^p$-norm of a FEM coefficient vector v over the nodes  or quadrature points in the elements on the given mesh. Note that for p=Inf, the values do not get inter- or extrapolated and thus it might not be true maximum over the domain, but only over the given data.
