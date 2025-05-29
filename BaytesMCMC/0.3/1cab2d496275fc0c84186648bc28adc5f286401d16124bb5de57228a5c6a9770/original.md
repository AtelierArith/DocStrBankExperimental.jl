```julia
mutable struct MALA{M<:BaytesDiff.ℓGradientResult, D<:BaytesDiff.AbstractDifferentiableTune} <: BaytesMCMC.MCMCKernel
```

MALA algorithm container.

# Fields

  * `result::BaytesDiff.ℓGradientResult`: Cached Result of last propagation step.
  * `diff::BaytesDiff.AbstractDifferentiableTune`: Differentiation tuning container
