```julia
mutable struct Metropolis{R<:BaytesDiff.ℓDensityResult} <: BaytesMCMC.MCMCKernel
```

Metropolis algorithm container.

# Fields

  * `result::BaytesDiff.ℓDensityResult`: Cached Result of last propagation step.
