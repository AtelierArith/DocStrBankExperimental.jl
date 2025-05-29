```
twonorm_boundary(
    v::AbstractVector{Float64},
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}(),
    qdim::Int64 = 1,
    order::Int64 = 3
)
```

Implementation of the discrete $L^2$-norm on the boundary based on a mass matrix. Faster version of pnorm for p=2 by using that direct assembly of mass matrix instead of basis matrices is possible. Assembles boundary mass matrix form mesh, boundary elements and the number of components. Then passes it to the base implementation of `twonorm`, which can be used for boundary terms as well.
