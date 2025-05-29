```
fdm_hermite_weights([TR=Rational{TI}], derivative_order::TI, accuracy_order::TI) where {TR<:Real, TI<:Integer}
```

Generate Hermite-type finite difference coefficients that include function value and derivative information.

# Arguments

  * `derivative_order::Integer`: The order of the derivative to approximate (must be ≥ 2)
  * `accuracy_order::Integer`: The desired order of accuracy

      * For derivative*order 2,3,6,7,10,11...: accuracy*order must be 4,8,12...
      * For derivative*order 4,5,8,9,12...: accuracy*order must be 2,6,10...

# Returns

Vector of rational coefficients for the Hermite-type finite difference stencil
