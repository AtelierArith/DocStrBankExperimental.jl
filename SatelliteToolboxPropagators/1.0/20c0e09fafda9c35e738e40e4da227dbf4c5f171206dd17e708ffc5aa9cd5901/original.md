```
struct J2PropagatorConstants{T<:Number}
```

Constants for the J2 orbit propagator.

# Fields

  * `R0::T`: Earth equatorial radius [m].
  * `μm::T`: √(GM / R0^3) [er/s]^(3/2).
  * `J2::T`: The second gravitational zonal harmonic of the Earth.
