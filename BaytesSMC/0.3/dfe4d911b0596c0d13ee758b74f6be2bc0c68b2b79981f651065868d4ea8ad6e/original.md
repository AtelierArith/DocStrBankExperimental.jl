```julia
struct SMC2Kernel{P<:BaytesFilters.ParticleFilter, M<:BaytesPMCMC.PMCMC} <: BaytesCore.AbstractAlgorithm
```

SMC2 Kernel, consisting of a kernel for the particle trajectory and kernel for all model parameter.

# Fields

  * `pf::BaytesFilters.ParticleFilter`: Kernel for (online) state propagation over time.
  * `pmcmc::BaytesPMCMC.PMCMC`: Kernel for jittering step.
