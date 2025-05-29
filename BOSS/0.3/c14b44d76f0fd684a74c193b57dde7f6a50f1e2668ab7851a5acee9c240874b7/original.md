```
SampleOptMAP(; kwargs...)
SampleOptMAP(::SamplingMAP, ::OptimizationMAP)
```

Combines `SamplingMAP` and `OptimizationMAP` to first sample many parameter samples from the prior, and subsequently start multiple optimization runs initialized from the best samples.

# Keywords

  * `samples::Int`: The number of drawn samples.
  * `algorithm::Any`: Defines the optimization algorithm.
  * `multistart::Int`: The number of optimization restarts.
  * `parallel::Bool`: If `parallel=true`, then both the sampling and the optimization are performed in parallel.
  * `softplus_hyperparams::Bool`: If `softplus_hyperparams=true` then the softplus function       is applied to GP hyperparameters (length-scales & amplitudes) and noise deviations       to ensure positive values during optimization.
  * `softplus_params::Union{Bool, Vector{Bool}}`: Defines to which parameters of the parametric       model should the softplus function be applied to ensure positive values.       Supplying a boolean instead of a binary vector turns the softplus on/off for all parameters.       Defaults to `false` meaning the softplus is applied to no parameters.
