```
runsampler(data,
options = MCMCOptionsList(),
params = PriorHyperparamsList();
verbose = true) -> MCMCResult
```

Runs the MCMC sampler on the data.

# Arguments

  * `data::MCMCData`: contains the distance matrix.
  * `options::MCMCOptionsList`: contains the number of iterations, burnin, etc.
  * `params::PriorHyperparamsList`: contains the prior hyperparameters for the model.
  * `verbose::Bool`: if false, disables all info messages and progress bars.

# Returns

A struct of type `MCMCResult` containing the MCMC samples, convergence diagnostics, and summary statistics.

# See also

[`MCMCData`](@ref), [`MCMCOptionsList`](@ref), [`fitprior`](@ref), [`PriorHyperparamsList`](@ref), [`MCMCResult`](@ref).
