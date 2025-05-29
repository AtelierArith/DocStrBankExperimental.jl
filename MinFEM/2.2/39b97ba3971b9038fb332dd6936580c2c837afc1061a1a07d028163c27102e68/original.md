```julia
quadrature_weights_boundary(
    d::Int64,
    order::Int64
) -> Union{Nothing, Vector{Float64}}

```

Returns weights of the Gauss-Legendre quadrature points  on the (d-1)-dimensional FEM reference element  for exact integration of polynomials up to the given order.
