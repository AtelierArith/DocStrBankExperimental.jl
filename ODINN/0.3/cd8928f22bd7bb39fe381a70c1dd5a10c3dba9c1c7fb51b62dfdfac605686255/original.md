```
InversionParameters{F<:AbstractFloat}(;
    initial_conditions::Vector{F} = [1.0],
    lower_bound::Vector{F} = [0.0],
    upper_bound::Vector{F} = [Inf],
    regions_split::Vector{Int} = [1, 1],
    x_tol::F = 1.0e-3,
    f_tol::F = 1.0e-3,
    solver = BFGS()
)
```

Initialize the parameters for the inversion process.

# Arguments

  * `initial_conditions::Vector{F}`: Starting point for optimization.
  * `lower_bound::Vector{F}`: Lower bounds for optimization variables.
  * `upper_bound::Vector{F}`: Upper bounds for optimization variables.
  * `regions_split::Vector{Int}`: Defines the amount of region split based on altitude and distance to border for the inversion process.
  * `x_tol::F`: Tolerance for variables convergence.
  * `f_tol::F`: Tolerance for function value convergence.
  * `solver`: Optimization solver to be used.
