```julia
struct DiagnosticsCustom{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

Default Configuration for Custom sampler.

# Fields

  * `ϵ::AbstractFloat`: Discretization size
