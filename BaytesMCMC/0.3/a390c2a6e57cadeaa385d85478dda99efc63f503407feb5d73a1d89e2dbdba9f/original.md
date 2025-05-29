```julia
struct DiagnosticsNUTS{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

Diagnostics fields for NUTS sampler.

# Fields

  * `ℓH::AbstractFloat`: Log density (negative energy).
  * `depth::Int64`: Depth of the tree.
  * `termination::BaytesMCMC.InvalidTree`: Reason for termination. See [`InvalidTree`](@ref) and [`REACHED_MAX_DEPTH`](@ref).
  * `acceptance_rate::AbstractFloat`: Acceptance rate statistic.
  * `ϵ::AbstractFloat`: Discretization size
  * `steps::Int64`: Number of leapfrog steps evaluated.
  * `directions::BaytesMCMC.Directions`: Directions for tree doubling (useful for debugging).
