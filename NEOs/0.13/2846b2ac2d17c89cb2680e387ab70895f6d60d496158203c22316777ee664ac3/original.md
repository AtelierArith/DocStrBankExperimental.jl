```
compute_delay(observatory::ObservatoryMPC{T}, t_r_utc::DateTime; kwargs...) where {T <: AbstractFloat}
```

Compute Taylor series expansion of time-delay observable around echo reception time. This allows to compute dopplers via automatic differentiation using

$$
\nu = -f\frac{d\tau}{dt},
$$

where $f$ is the transmitter frequency (MHz) and $\tau$ is the time-delay at reception time $t$. Computed values include corrections due to Earth orientation, LOD and polar motion.

**Note:** Works only with `TaylorInterpolant` ephemeris. See [`PlanetaryEphemeris.TaylorInterpolant`](@ref).

# Arguments

  * `observatory::ObservatoryMPC{T}`: observing station.
  * `t_r_utc::DateTime`: UTC time of echo reception.

# Keyword arguments

  * `tord::Int = 5`: order of Taylor expansions.
  * `niter::Int = 10`: number of light-time solution iterations.
  * `xve::EarthEph = earthposvel`: Earth ephemeris.
  * `xvs::SunEph = sunposvel`: Sun ephemeris.
  * `xva::AstEph`: asteroid ephemeris.

All ephemeris must take  [et seconds since J2000] and return [barycentric position in km and velocity in km/sec].

!!! reference
    See https://doi.org/10.1086/116062.

