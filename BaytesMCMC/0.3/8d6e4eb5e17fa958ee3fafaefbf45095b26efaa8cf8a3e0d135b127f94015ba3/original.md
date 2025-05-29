```julia
struct MCMCDiagnostics{P, K<:BaytesMCMC.MCMCKernelDiagnostics, G, A} <: BaytesCore.AbstractDiagnostics
```

MCMC Diagnostics container.

# Fields

  * `base::BaytesCore.BaseDiagnostics`: Diagnostics used for all Baytes kernels
  * `kernel::BaytesMCMC.MCMCKernelDiagnostics`: Kernel specific diagnostics.
  * `divergence::Bool`: Boolean if diverged.
  * `accept::BaytesCore.AcceptStatistic`: Acceptance Rate of current step.
  * `generated::Any`: Generated quantities specified for objective
  * `generated_algorithm::Any`: Generated quantities specified for algorithm
