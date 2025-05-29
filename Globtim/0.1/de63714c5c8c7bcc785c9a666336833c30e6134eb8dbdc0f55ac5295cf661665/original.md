```
struct ApproxPoly
```

A structure to represent the polynomial approximation and related data.

# Fields

  * `coeffs::Vector`: The coefficients of the polynomial approximation. Could be floats or Big

rationals.  _ `degree::Int`: The degree of the polynomial approximation.

  * `nrm::Float64`: The norm of the polynomial approximation.
  * `N::Int`: The number of grid points used in the approximation.
  * `scale_factor::Float64`: The scaling factor applied to the domain.
  * `grid::Matrix{Float64}`: The grid of points used in the approximation.
  * `z::Vector{Float64}`: The values of the function objective at the grid points.

# Description

The `ApproxPoly` struct is used to store the results of a polynomial approximation, including the coefficients of the polynomial, the norm of the approximation, the number of grid points, the scaling factor, the grid of points, and the values of the function at the grid points.
