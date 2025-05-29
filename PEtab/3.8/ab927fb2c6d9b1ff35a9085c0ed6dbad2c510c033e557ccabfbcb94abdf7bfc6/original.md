```
solve_all_conditions(x, prob::PEtabODEProblem, solver; kwargs)
```

Solve the ODE model in `prob` for all simulation conditions with the provided ODE-solver.

`x` should be a `Vector` or `ComponentArray` with parameters in the order expected by `prob` (see [`get_x`](@ref)).

# Keyword Arguments

  * `abstol=1e-8`: Absolute tolerance for the ODE solver.
  * `reltol=1e-8`: Relative tolerance for the ODE solver.
  * `maxiters=1e4`: Maximum iterations for the ODE solver.
  * `ntimepoints_save=0`: The number of time points at which to save the ODE solution for   each condition. A value of 0 means the solution is saved at the solvers default time   points.
  * `save_observed_t=false`: When set to true, this option overrides `ntimepoints_save`   and saves the ODE solution only at the time points where measurement data is available.

# Returns

  * `odesols`: A dictionary containing the `ODESolution` for each simulation condition.
