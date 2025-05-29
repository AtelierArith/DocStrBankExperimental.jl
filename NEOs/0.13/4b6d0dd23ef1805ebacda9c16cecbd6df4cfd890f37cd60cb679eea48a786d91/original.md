```
residuals(obs::Vector{RadarJPL{T}}; kwargs...)  where {T <: AbstractFloat}
```

Compute O-C residuals for radar astrometry, including corrections due to Earth orientation, LOD and polar motion.

See also [`compute_delay`](@ref) and [`radar_astrometry`](@ref).

# Arguments

  * `obs::Vector{RadarJPL{T}}`: vector of observations.

# Keyword arguments

  * `tc::Real = 1.0`: time offset wrt echo reception time, to compute Doppler shifts by range differences (seconds). Offsets will be rounded to the nearest millisecond.
  * `autodiff::Bool = true`: whether to compute Doppler shift via automatic diff of [`compute_delay`](@ref) or not.
  * `tord::Int = 5`: order of Taylor expansions.
  * `niter::Int = 10`: number of light-time solution iterations.
  * `xve::EarthEph = earthposvel`: Earth ephemeris.
  * `xvs::SunEph = sunposvel`: Sun ephemeris.
  * `xva::AstEph`: asteroid ephemeris.

All ephemeris must take [et seconds since J2000] and return [barycentric position in km and velocity in km/sec].
