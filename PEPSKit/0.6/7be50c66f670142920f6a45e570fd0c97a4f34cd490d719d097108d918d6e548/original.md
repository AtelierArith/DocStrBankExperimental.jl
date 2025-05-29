```julia
struct SimultaneousCTMRG <: PEPSKit.CTMRGAlgorithm
```

CTMRG algorithm where all sides are grown and renormalized at the same time. In particular, the projectors are applied to the corners from two sides simultaneously.

## Fields

  * `tol::Float64`
  * `maxiter::Int64`
  * `miniter::Int64`
  * `verbosity::Int64`
  * `projector_alg::PEPSKit.ProjectorAlgorithm`

## Constructors

```
SimultaneousCTMRG(; kwargs...)
```

Construct a simultaneous CTMRG algorithm struct based on keyword arguments. For a full description, see [`leading_boundary`](@ref). The supported keywords are:

  * `tol::Real=1.0e-8`
  * `maxiter::Int=100`
  * `miniter::Int=4`
  * `verbosity::Int=2`
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)`
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}`
  * `projector_alg::Symbol=:halfinfinite`
