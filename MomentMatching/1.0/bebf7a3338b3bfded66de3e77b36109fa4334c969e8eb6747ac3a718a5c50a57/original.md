```julia
struct NumParMM{S<:AbstractFloat, T<:Integer}
```

# Description

Structure to store numerical parameters for estimation procedure.

# Fields

  * `sobolinds`: Indexes of Sobol points to use
  * `Nloc`: # of best points to evaluate for local stage of estimation (or to save if only global stage, see [`matchmom`](@ref))
  * `full_lb_global`: Lower bound for parameters in global stage
  * `full_ub_global`: Upper bound for parameters in global stage
  * `onlyglo`: Logical, true if only global optimization is to be performed
  * `onlyloc`: Logical, true if only local optimization is to be performed
  * `local_opt_settings`: Settings for optimization used in local stage
