```
struct J4PropagatorConstants{T<:Number}
```

Constants for the J4 orbit propagator.

# Fields

  * `R0::T`: Earth equatorial radius [m].
  * `μm::T`: √(GM / R0^3) [er/s]^(3/2).
  * `J2::T`: The second gravitational zonal harmonic of the Earth.
  * `J4::T`: The fourth gravitational zonal harmonic of the Earth.
