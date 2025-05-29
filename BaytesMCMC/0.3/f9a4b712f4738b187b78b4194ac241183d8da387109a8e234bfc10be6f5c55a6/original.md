```julia
mutable struct NUTS{R<:BaytesDiff.ℓObjectiveResult, D<:BaytesDiff.AbstractDifferentiableTune, C<:BaytesMCMC.KineticEnergy} <: BaytesMCMC.MCMCKernel
```

NUTS - Container used throughout sampling process.

# Fields

  * `result::BaytesDiff.ℓObjectiveResult`: Target result stored for caching.
  * `diff::BaytesDiff.AbstractDifferentiableTune`: Differentiation tuning struct.
  * `energy::BaytesMCMC.KineticEnergy`: Energy used for Hamiltonian.
  * `max_depth::Int64`: Maximum tree depth for U-Turn
