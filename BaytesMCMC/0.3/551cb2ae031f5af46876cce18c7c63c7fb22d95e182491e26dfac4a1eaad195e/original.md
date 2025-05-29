```julia
struct DiagnosticsHMC{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

Diagnostics fields for HMC sampler.

# Fields

  * `ϵ::AbstractFloat`: Discretization size
  * `steps::Int64`: Number of Leapfrog steps
