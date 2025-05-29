```
struct Sgp4Constants{T}
```

Gravitational constants for SGP4.

# Fields

  * `R0::T`: Earth equatorial radius [km].
  * `XKE::T`: 60 ⋅ √(GM / R0^3) [er/min]^(3/2).
  * `J2::T`: The second gravitational zonal harmonic of the Earth.
  * `J3::T`: The thrid gravitational zonal harmonic of the Earth.
  * `J4::T`: The fourth gravitational zonal harmonic of the Earth.
