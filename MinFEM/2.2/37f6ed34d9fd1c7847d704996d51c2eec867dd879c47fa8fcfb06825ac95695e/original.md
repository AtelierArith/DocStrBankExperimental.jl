```julia
quadrature_points(
    element::Int64,
    mesh::MinFEM.Mesh,
    order::Int64
) -> Vector{Vector{Float64}}

```

Returns global coordinates of the Gauss-Legendre quadrature points  on a specified element in the given mesh for exact integration of polynomials up to the given order.
