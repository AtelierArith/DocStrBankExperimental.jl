```julia
struct DiagnosticsMALA{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

Diagnostics for MALA sampler.

# Fields

  * `ϵ::AbstractFloat`: Discretization size
