This function is used to setup the linear system for the regression problem. It returns the matrix A and the vector b, such that A*x = b, where x is the vector of parameters.

```
setup_linear_system(sys::AbstractTimeDependentSystem)
```

# Arguments

  * `sys`: The system of equations to be solved for the parameters (ODESystem or DAESystem)

# Returns

  * `A`: The symbolic matrix A in the equation A*x = b
  * `b`: The symbolic vector b in the equation A*x = b
