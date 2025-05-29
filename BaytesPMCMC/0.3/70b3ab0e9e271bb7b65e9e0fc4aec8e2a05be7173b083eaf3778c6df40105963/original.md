```julia
struct PMCMCDiagnostics{T, P<:BaytesFilters.ParticleFilterDiagnostics, M<:BaytesMCMC.MCMCDiagnostics} <: BaytesCore.AbstractDiagnostics
```

Contains information about log-likelihood, expected sample size and proposal trajectory.

# Fields

  * `base::BaytesCore.BaseDiagnostics`: Diagnostics used for all Baytes kernels
  * `pf::BaytesFilters.ParticleFilterDiagnostics`: Particle Filter diagnostics.
  * `mcmc::BaytesMCMC.MCMCDiagnostics`: MCMC diagnostics.
