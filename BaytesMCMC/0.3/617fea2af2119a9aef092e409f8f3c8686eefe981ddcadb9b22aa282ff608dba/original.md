```julia
struct MCMCTune{A<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool, F<:AbstractFloat, T<:ModelWrappers.Tagged, E<:Tuple, P<:BaytesMCMC.Proposal} <: BaytesCore.AbstractTune
```

MCMC Tuning container.

# Fields

  * `tagged::ModelWrappers.Tagged`: Tagged Parameter.
  * `phase::BaytesMCMC.PhaseTune`: Current Phase in MCMC Cycle
  * `stepsize::BaytesMCMC.StepSizeTune`: Stepsize container
  * `proposal::BaytesMCMC.Proposal`: Information for posterior covariance estimate
  * `generated::BaytesCore.UpdateBool`: Boolean if generated quantities should be generated while sampling
  * `iter::BaytesCore.Iterator`: Current iteration number
