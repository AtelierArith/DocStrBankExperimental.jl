```
InversionParameters{F<:AbstractFloat}
```

A mutable struct that holds parameters for inversion processes. This struct is a subtype of `AbstractParameters`.

# Fields

  * `initial_conditions::Vector{F}`: A vector of initial conditions.
  * `lower_bound::Vector{F}`: A vector specifying the lower bounds for the parameters.
  * `upper_bound::Vector{F}`: A vector specifying the upper bounds for the parameters.
  * `regions_split::Vector{Int}`: A vector indicating how the regions are split.
  * `x_tol::F`: The tolerance for the solution's x-values.
  * `f_tol::F`: The tolerance for the function values.
  * `solver::Any`: The solver to be used for the inversion process.
