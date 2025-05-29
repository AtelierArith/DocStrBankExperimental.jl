```
quadrature_points_boundary(
    mesh::Mesh,
    order::Int64;
    boundaryElements::Set{Int64} = Set{Int64}()
)-> Array{Array{Float64,1},1}
```

Returns global coordinates of the Gauss-Legendre quadrature points  on each boundary element in the given mesh for exact integration of polynomials up to the given order.
