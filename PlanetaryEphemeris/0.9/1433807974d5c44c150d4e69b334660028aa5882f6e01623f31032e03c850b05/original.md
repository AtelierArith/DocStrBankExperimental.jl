```
selecteph(eph::TaylorInterpolant, bodyind::Union{Int, AbstractVector{Int}}, t0::T = eph.t0,
          tf::T = eph.t0 + eph.t[end]; euler::Bool = false, ttmtdb::Bool = false) where {T <: Real}
```

Return a subset of `eph` with only the ephemeris of bodies `bodyind` in timerange `[t0, tf]`. The keyword arguments allow to include lunar euler angles and/or TT-TDB.
