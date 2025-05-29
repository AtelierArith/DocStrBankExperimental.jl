```
getoffset(TDB, TT, second, fraction[, eop])
```

Return the offset between [`TDB`](@ref) and [`TT`](@ref) for the current epoch (`second` after J2000 and `fraction`) for an observer on earth in seconds.

### Arguments

  * `second`, `fraction`: Current epoch
  * `elong`: Longitude (east positive, radians)
  * `u`: Distance from Earth's spin axis (km)
  * `v`: Distance north of equatorial plane (km)

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TDB, TT, 0, 0.0, π, 6371.0, 0.0)
9.928419814106208e-5
```

### References

  * [ERFA](https://github.com/liberfa/erfa/blob/master/src/dtdb.c)
