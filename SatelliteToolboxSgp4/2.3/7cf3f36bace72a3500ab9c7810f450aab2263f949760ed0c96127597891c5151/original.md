```
sgp4_init!(sgp4d::Sgp4Propagator{Tepoch, T}, epoch::Number, n₀::Number, e₀::Number, i₀::Number, Ω₀::Number, ω₀::Number, M₀::Number, bstar::Number) where {Tepoch, T} -> Nothing
sgp4_init!(sgp4d::Sgp4Propagator{Tepoch, T}, tle::TLE) where {Tepoch, T} -> Nothing
```

Initialize the SGP4 data structure `sgp4d` with the initial orbit specified by the arguments.

!!! warning
    The propagation constants `sgp4c::Sgp4PropagatorConstants` in `sgp4d` will not be changed. Hence, they must be initialized.


# Arguments

  * `epoch::Number`: Epoch of the orbital elements [Julian Day].
  * `n₀::Number`: SGP type "mean" mean motion at epoch [rad/min].
  * `e₀::Number`: "Mean" eccentricity at epoch.
  * `i₀::Number`: "Mean" inclination at epoch [rad].
  * `Ω₀::Number`: "Mean" longitude of the ascending node at epoch [rad].
  * `ω₀::Number`: "Mean" argument of perigee at epoch [rad].
  * `M₀::Number`: "Mean" mean anomaly at epoch [rad].
  * `bstar::Number`: Drag parameter (B*).
  * `tle::TLE`: TLE to initialize the SPG4 (see `TLE`).
