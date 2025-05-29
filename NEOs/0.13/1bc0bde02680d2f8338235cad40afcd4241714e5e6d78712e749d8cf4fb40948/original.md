```
residuals(radec::AbstractVector{RadecMPC{T}}, w8s::AbstractVector{Tuple{T, T}},
    bias::AbstractVector{Tuple{T, T}}; xva::AstEph,
    kwargs...) where {AstEph, T <: Real}
```

Compute observed minus computed residuals for optical astrometry `radec`. Corrections due to Earth orientation, LOD and polar motion are computed by default.

See also [`OpticalResidual`](@ref) and [`compute_radec`](@ref).

## Arguments

  * `radec::AbstractVector{RadecMPC{T}}`: optical astrometry.
  * `w8s::AbstractVector{Tuple{T, T}}`: statistical weights.
  * `bias::AbstractVector{Tuple{T, T}}`: debiasing corrections.

## Keyword arguments

  * `niter::Int`: number of light-time solution iterations (default: `5`).
  * `xve::EarthEph`: Earth ephemeris (default: `earthposvel`).
  * `xvs::SunEph`: Sun ephemeris (default: `sunposvel`).
  * `xva::AstEph`: asteroid ephemeris.

All ephemeris must take [et seconds since J2000] and return [barycentric position in km and velocity in km/sec].
