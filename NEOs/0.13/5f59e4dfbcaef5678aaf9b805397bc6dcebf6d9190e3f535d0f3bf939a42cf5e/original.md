```
compute_radec(observatory::ObservatoryMPC{T}, t_r_utc::DateTime; kwargs...)
compute_radec(obs::RadecMPC{T}; kwargs...)
compute_radec(obs::Vector{RadecMPC{T}}; kwargs...) where {T <: Real}
```

Compute astrometric right ascension and declination [arcsec] for a set of MPC-formatted observations. Corrections due to Earth orientation, LOD and polar motion are considered in computations.

## Arguments

  * `observatory::ObservatoryMPC{T}`: observation site.
  * `t_r_utc::DateTime`: UTC time of astrometric observation.
  * `obs::Vector{RadecMPC{T}}`: optical observation(s).

## Keyword arguments

  * `niter::Int`: number of light-time solution iterations (default: `5`).
  * `xve::EarthEph`: Earth ephemeris (default: `earthposvel`).
  * `xvs::SunEph`: Sun ephemeris (default: `sunposvel`).
  * `xva::AstEph`: asteroid ephemeris.

All ephemeris must take [et seconds since J2000] and return [barycentric position in km and velocity in km/sec].
