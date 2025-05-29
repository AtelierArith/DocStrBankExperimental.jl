```
OptimizationMAP(; kwargs...)
```

Finds the MAP estimate of the model parameters and hyperparameters using the Optimization.jl package.

# Keywords

  * `algorithm::Any`: Defines the optimization algorithm.
  * `multistart::Union{Int, Matrix{Float64}}`: The number of optimization restarts,       or a vector of tuples `(θ, λ, α)` containing initial (hyper)parameter values for the optimization runs.
  * `parallel::Bool`: If `parallel=true` then the individual restarts are run in parallel.
  * `softplus_hyperparams::Bool`: If `softplus_hyperparams=true` then the softplus function       is applied to GP hyperparameters (length-scales & amplitudes) and noise deviations       to ensure positive values during optimization.
  * `softplus_params::Union{Bool, Vector{Bool}}`: Defines to which parameters of the parametric       model should the softplus function be applied to ensure positive values.       Supplying a boolean instead of a binary vector turns the softplus on/off for all parameters.       Defaults to `false` meaning the softplus is applied to no parameters.
