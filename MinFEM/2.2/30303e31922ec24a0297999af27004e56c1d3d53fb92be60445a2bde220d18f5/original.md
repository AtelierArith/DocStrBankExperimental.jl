```julia
quadrature_points(
    d::Int64,
    order::Int64
) -> Union{Nothing, Vector{Vector{Float64}}}

```

Returns coordinates of the Gauss-Legendre quadrature points  on the d-dimensional FEM reference element  for exact integration of polynomials up to the given order.
