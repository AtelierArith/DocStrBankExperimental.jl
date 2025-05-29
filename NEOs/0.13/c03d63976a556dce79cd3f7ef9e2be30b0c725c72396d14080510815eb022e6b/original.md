```
radar_astrometry(observatory::ObservatoryMPC{T}, t_r_utc::DateTime, F_tx::Real; kwargs...) where {T <: AbstractFloat}
radar_astrometry(radar::RadarJPL{T}; kwargs...) where {T <: AbstractFloat}
radar_astrometry(astradarfile::String; kwargs...)
radar_astrometry(astradardata::Vector{RadarJPL}; kwargs...) where {T <: AbstractFloat}
```

Return time-delay and Doppler shift.

# Arguments

  * `observatory::ObservatoryMPC{T}`: observing station.
  * `t_r_utc::DateTime`: UTC time of echo reception.
  * `F_tx::Real`: transmitter frequency (MHz).
  * `radar::RadarJPL{T}` / `astradardata::Vector{RadarJPL{T}}`: radar observation(s).
  * `astradarfile::String`: file where to retrieve radar observations.

# Keyword arguments

  * `tc::Real = 1.0`: time offset wrt echo reception time, to compute Doppler shifts by range differences (seconds). Offsets will be rounded to the nearest millisecond.
  * `autodiff::Bool = true`: whether to compute Doppler shift via automatic diff of [`compute_delay`](@ref) or not.
  * `tord::Int = 5`: order of Taylor expansions.
  * `niter::Int = 10`: number of light-time solution iterations.
  * `xve::EarthEph = earthposvel`: Earth ephemeris.
  * `xvs::SunEph = sunposvel`: Sun ephemeris.
  * `xva::AstEph`: asteroid ephemeris.

All ephemeris must take  [et seconds since J2000] and return [barycentric position in km and velocity in km/sec].
