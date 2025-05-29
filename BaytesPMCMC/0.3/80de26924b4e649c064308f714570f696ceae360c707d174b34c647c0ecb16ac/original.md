```julia
struct PMCMC{M<:BaytesPMCMC.PMCMCKernel, N<:BaytesPMCMC.PMCMCTune} <: BaytesCore.AbstractAlgorithm
```

Particle MCMC container, container kernel and tuning.

# Fields

  * `kernel::BaytesPMCMC.PMCMCKernel`: PMCMC sampler
  * `tune::BaytesPMCMC.PMCMCTune`: Tuning configuration for kernel.
