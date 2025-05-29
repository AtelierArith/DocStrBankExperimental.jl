```julia
struct MCMCDefault{K<:NamedTuple, S<:BaytesMCMC.ConfigStepsize, P<:BaytesMCMC.ConfigProposal, G, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Default arguments for MCMC constructor.

# Fields

  * `kernel::NamedTuple`: Individual keyword arguments for tuning different MCMC kernels.
  * `stepsize::BaytesMCMC.ConfigStepsize`: Stepsize default configuration for adaption.
  * `proposal::BaytesMCMC.ConfigProposal`: Proposal distribution default configuration for adaption.
  * `GradientBackend::Any`: Gradient backend used in MCMC step. Not used if Metropolis sampler is chosen.
  * `init::ModelWrappers.AbstractInitialization`: Method to obtain initial Modelparameter, see 'AbstractInitialization'.
  * `generated::BaytesCore.UpdateBool`: Boolean if generate(_rng, objective) for corresponding model is stored in MCMC Diagnostics.
