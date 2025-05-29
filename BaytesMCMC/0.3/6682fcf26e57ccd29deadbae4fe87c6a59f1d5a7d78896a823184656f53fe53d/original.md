```julia
mutable struct Custom{R<:BaytesDiff.ℓDensityResult, P} <: BaytesMCMC.MCMCKernel
```

Custom algorithm container.

# Fields

  * `result::BaytesDiff.ℓDensityResult`: Cached Result of last propagation step.
  * `proposal::Any`: Callable struct/closure/function of `result.θᵤ` that returns proposal distribution.
