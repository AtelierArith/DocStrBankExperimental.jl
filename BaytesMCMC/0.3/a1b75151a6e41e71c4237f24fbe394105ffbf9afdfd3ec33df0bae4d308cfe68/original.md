```julia
struct DiagnosticsMetropolis{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

Default Configuration for Metropolis sampler.

# Fields

  * `ϵ::AbstractFloat`: Discretization size
