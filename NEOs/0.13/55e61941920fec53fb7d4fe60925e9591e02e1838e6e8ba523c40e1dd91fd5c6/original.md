```
loadpeeph(eph::TaylorInterpolant = sseph, t_0::T = sseph.t0,
          t_f::S = sseph.t0 + sseph.t[end]) where {T, S <: Real}
```

Load ephemeris produced by `PlanetaryEphemeris.jl` in timerange `[t_0, t_f] ⊆ [0.0, 36525.0]` where `t` must have units of TDB days since J2000. The available options for `eph` are:

  * `NEOs.sseph`: Solar system ephemeris.
  * `NEOs.acceph`: accelerations ephemeris.
  * `NEOs.poteph`: newtonian potentials ephemeris.

!!! warning
    Running this function for the first time will download the `sseph_p100` artifact (885 MB) which can take several minutes.

