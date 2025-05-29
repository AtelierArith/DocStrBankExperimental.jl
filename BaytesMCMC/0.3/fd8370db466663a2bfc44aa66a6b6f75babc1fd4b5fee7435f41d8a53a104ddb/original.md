```julia
mutable struct HMC{R<:BaytesDiff.ℓObjectiveResult, D<:BaytesDiff.AbstractDifferentiableTune, C<:BaytesMCMC.KineticEnergy, T<:BaytesCore.UpdateBool} <: BaytesMCMC.MCMCKernel
```

HMC - Container used throughout sampling process.

# Fields

  * `result::BaytesDiff.ℓObjectiveResult`: Target result stored for caching.
  * `diff::BaytesDiff.AbstractDifferentiableTune`: Differentiation tuning struct.
  * `energy::BaytesMCMC.KineticEnergy`: Energy used for Hamiltonian.
  * `stepnumber::BaytesMCMC.StepNumberTune`: Tuning struct for discretization steps
