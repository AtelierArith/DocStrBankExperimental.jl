```
struct SequentialCTMRG <: CTMRGAlgorithm
```

CTMRG algorithm where the expansions and renormalization is performed sequentially column-wise. This is implemented as a growing and projecting step to the left, followed by a clockwise rotation (performed four times).

## Fields

  * `tol::Float64`
  * `maxiter::Int64`
  * `miniter::Int64`
  * `verbosity::Int64`
  * `projector_alg::PEPSKit.ProjectorAlgorithm`

## Constructors

```
SequentialCTMRG(; kwargs...)
```

Construct a sequential CTMRG algorithm struct based on keyword arguments. For a full description, see [`leading_boundary`](@ref). The supported keywords are:

  * `tol::Real=1.0e-8`
  * `maxiter::Int=100`
  * `miniter::Int=4`
  * `verbosity::Int=2`
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)`
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}`
  * `projector_alg::Symbol=:halfinfinite`
