```julia
struct HalfInfiniteProjector{S<:PEPSKit.SVDAdjoint, T} <: PEPSKit.ProjectorAlgorithm
```

Projector algorithm implementing projectors from SVDing the half-infinite CTMRG environment.

## Fields

  * `svd_alg::PEPSKit.SVDAdjoint`
  * `trscheme::Any`
  * `verbosity::Int64`

## Constructors

```
HalfInfiniteProjector(; kwargs...)
```

Construct the half-infinite projector algorithm based on the following keyword arguments:

  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}=SVDAdjoint()` : SVD algorithm including the reverse rule. See [`SVDAdjoint`](@ref).
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)` : Truncation scheme for the projector computation, which controls the resulting virtual spaces. Here, `alg` can be one of the following:

      * `:fixedspace` : Keep virtual spaces fixed during projection
      * `:notrunc` : No singular values are truncated and the performed SVDs are exact
      * `:truncerr` : Additionally supply error threshold `η`; truncate to the maximal virtual dimension of `η`
      * `:truncdim` : Additionally supply truncation dimension `η`; truncate such that the 2-norm of the truncated values is smaller than `η`
      * `:truncspace` : Additionally supply truncation space `η`; truncate according to the supplied vector space
      * `:truncbelow` : Additionally supply singular value cutoff `η`; truncate such that every retained singular value is larger than `η`
  * `verbosity::Int=0` : Projector output verbosity which can be:

    0. Suppress output information
    1. Print singular value degeneracy warnings
