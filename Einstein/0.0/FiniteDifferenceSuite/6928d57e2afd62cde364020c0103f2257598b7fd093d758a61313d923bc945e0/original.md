```
fdm_dissipation_operator([TR=Float64], dissipation_order::TI, σ::TR, dx::TR) -> FiniteDifferenceDerivativeOperator{TR}
```

Create a finite difference dissipation operator with specified dissipation order.

# Arguments

  * `TR`: The element type of the operator
  * `dissipation_order::Integer`: The order of the dissipation operator
  * `σ::TR`: The dissipation coefficient
  * `dx::TR`: The grid spacing
