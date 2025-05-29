```julia
mutable struct StepSizeTune{A<:BaytesCore.UpdateBool, F<:AbstractFloat}
```

Tuning stepsize parameter for MCMC algorithm.

# Fields

  * `adaption::BaytesCore.UpdateBool`: If true, stepsize will be adapted.
  * `dualaverage::BaytesMCMC.DualAverage`: Dualaverage struct
  * `ϵ::AbstractFloat`: Current stepsize
