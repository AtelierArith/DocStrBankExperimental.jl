```julia
struct ParticleGibbs{P<:BaytesFilters.ParticleFilter, M<:BaytesMCMC.MCMC} <: BaytesPMCMC.PMCMCKernel
```

Default arguments for PMCMC constructor.

# Fields

  * `pf::BaytesFilters.ParticleFilter`: Particle Filter kernel to estimate latent trajectory.
  * `mcmc::BaytesMCMC.MCMC`: MCMC kernel to sample continuous model parameter.
