```
KeplerianElements{Tepoch<:Number, T<:Number} <: Orbit{Tepoch, T}
```

This structure defines the orbit in terms of the Keplerian elements.

# Fields

  * `t::Tepoch`: Epoch.
  * `a::T`: Semi-major axis [m].
  * `e::T`: Eccentricity [ ].
  * `i::T`: Inclination [rad].
  * `Ω::T`: Right ascension of the ascending node [rad].
  * `ω::T`: Argument of perigee [rad].
  * `f::T`: True anomaly [rad].
