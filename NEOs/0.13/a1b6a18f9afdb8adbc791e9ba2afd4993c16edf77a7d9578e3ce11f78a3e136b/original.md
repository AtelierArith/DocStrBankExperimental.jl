```
bwdfwdeph(t::U, bwd::TaylorInterpolant, fwd::TaylorInterpolant
    [, et::Bool [, kmsec::Bool]]) where {U <: Number}
```

Evaluate an ephemerides at time `t`, where `bwd` (`fwd`) is the backward (forward) propagation.

## Optional arguments

  * `et::Bool`: whether `t` is in ephemeris seconds since J2000 (default: `true`).
  * `kmsec::Bool`: whether to convert the state vector to [km, km/s](default: `true`).
