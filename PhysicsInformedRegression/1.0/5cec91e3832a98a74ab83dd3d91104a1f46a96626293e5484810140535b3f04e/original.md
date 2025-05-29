This function is used to solve the regression problem. It returns the vector of parameters.

```
physics_informed_regression(sys::AbstractTimeDependentSystem, u::Vector, du::Vector)
physics_informed_regression(sys::AbstractTimeDependentSystem, u::Vector, du::Vector, A::Matrix, b::Vector)
kwargs: lambda = 0.0 (regularization parameter)
```

# Arguments

  * `sys`: The system of equations to be solved for the parameters (ODESystem or DAESystem)
  * `u`: The vector of states
  * `du`: The vector of derivatives
  * `A`: The symbolic matrix A in the equation A*x = b
  * `b`: The symbolic vector b in the equation A*x = b

# Returns

  * `paramsest`: The vector of estimated parameters
