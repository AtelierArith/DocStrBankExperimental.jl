```julia
quadrature_points(
    mesh::MinFEM.Mesh,
    order::Int64
) -> Vector{Vector{Float64}}

```

Returns global coordinates of the Gauss-Legendre quadrature points  on each finite element in the given mesh for exact integration of polynomials up to the given order.
