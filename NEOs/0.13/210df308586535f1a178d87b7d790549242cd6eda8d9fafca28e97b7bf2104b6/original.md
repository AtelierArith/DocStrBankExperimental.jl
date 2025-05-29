```
outlier_rejection!(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x::Vector{T}, Γ::Matrix{T} [, cache::OutlierRejectionCache{T}];
    kwargs...) where {T <: Real}
```

Carpino et al. (2003) outlier rejection algorithm.

See also [`carpino_smoothing`](@ref).

## Arguments

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: vector of residuals.
  * `x::Vector{T}`: evaluation deltas.
  * `Γ::Matrix{T}`: covariance matrix.
  * `cache::OutlierRejectionCache{T}`: see [`OutlierRejectionCache`](@ref).

## Keyword arguments

  * `χ2_rec::T`: recovery threshold (default: `7.0`).
  * `χ2_rej::T`: rejection threshold (default: `8.0`).
  * `fudge::T`: rejection fudge term coefficient (default: `400.0`).
  * `α::T`: scaling factor for maximum chi (default: `0.25`).
  * `max_per::T`: maximum allowed drop percentage (default: `10.0`).

!!! reference
    See https://doi.org/10.1016/S0019-1035(03)00051-4.

