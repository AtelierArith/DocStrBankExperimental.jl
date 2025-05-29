```
r_tod_to_mod_fk5([T, ]jd_tt::Number[, δΔϵ_1980::Number, δΔψ_1980::Number]) -> T
```

Compute the rotation that aligns the True of Date (TOD) frame with the Mean of Date (MOD) frame at the Julian Day `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-76/FK5 theory. Notice that one can provide corrections for the nutation in obliquity (`δΔϵ_1980`) [rad] and in longitude (`δΔψ_1980`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the TOD frame with the MOD frame.

# Remarks

The True of Date (TOD) frame is rotated into the Mean of Date (MOD) frame considering the 1980 IAU Theory of Nutation. The IERS EOP corrections must be added if one wants to make the rotation consistent with the Geocentric Celestial Reference Systems (GCRS).
