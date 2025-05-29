```
fdm_boundary_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

Generate finite difference coefficients for shifted boundary conditions.

# Arguments

  * `derivative_order::Integer`: The order of the derivative to approximate
  * `accuracy_order::Integer`: The desired order of accuracy

# Returns

Tuple of left and right shifted boundary finite difference coefficients The coefficients are stored in a matrix with the rows representing the different grid points. The rows are ordered from the leftmost grid point to the rightmost grid point.
