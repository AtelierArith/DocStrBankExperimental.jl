```julia
struct MCMC{M<:BaytesMCMC.MCMCKernel, N<:BaytesMCMC.MCMCTune} <: BaytesCore.AbstractAlgorithm
```

Stores information for proposal step.

# Fields

  * `kernel::BaytesMCMC.MCMCKernel`: MCMC sampler
  * `tune::BaytesMCMC.MCMCTune`: Tuning configuration for kernel.
