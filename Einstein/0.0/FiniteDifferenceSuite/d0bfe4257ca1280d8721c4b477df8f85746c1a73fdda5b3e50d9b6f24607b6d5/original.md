```
fdm_derivative_operator([TR=Float64], derivative_order::Integer, accuracy_order::Integer, dx::TR) -> FiniteDifferenceDerivativeOperator{TR}
```

Create a finite difference derivative operator with specified derivative and accuracy orders.

# Arguments

  * `TR`: The element type of the operator
  * `derivative_order::Integer`: The order of the derivative
  * `accuracy_order::Integer`: The order of accuracy
  * `dx::TR`: The grid spacing
