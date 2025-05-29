```
getoffset(TT, TDB, second, fraction[, eop])
```

Return the offset between [`TT`](@ref) and [`TDB`](@ref) for the current epoch (`second` after J2000 and `fraction`) for an observer on earth in seconds.

### Arguments

  * `second`, `fraction`: Current epoch
  * `elong`: Longitude (east positive, radians)
  * `u`: Distance from Earth's spin axis (km)
  * `v`: Distance north of equatorial plane (km)

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TDB, 0, 0.0, π, 6371.0, 0.0)
-9.928419818977206e-5
```

### References

  * [ERFA](https://github.com/liberfa/erfa/blob/master/src/dtdb.c)
