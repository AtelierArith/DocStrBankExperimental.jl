```
fdm_central_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

Generate central finite difference coefficients for a given derivative and accuracy order.

# Arguments

  * `derivative_order::Integer`: The order of the derivative to approximate
  * `accuracy_order::Integer`: The desired order of accuracy (must be even)

# Returns

Vector of rational coefficients for the finite difference stencil
