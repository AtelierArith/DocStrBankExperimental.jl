```
r_mod_to_pef_fk5([T, ]jd_ut1::Number, jd_tt::Number[, δΔϵ_1980::Number, δΔψ_1980::Number]) -> T
```

Compute the rotation that aligns the Mean of Date (MOD) reference frame with the Pseudo-Earth Fixed (PEF) frame at the Julian Day `jd_ut1` [UT1] and `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-76/FK5 theory. Notice that one can provide corrections for the nutation in obliquity (`δΔϵ_1980`) [rad] and in longitude (`δΔψ_1980`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

The Julian Day in UT1 is used to compute the Greenwich Mean Sidereal Time (GMST) (see `jd_to_gmst`), whereas the Julian Day in Terrestrial Time is used to compute the nutation in the longitude. Notice that the Julian Day in UT1 and in Terrestrial Time must be equivalent, i.e. must be related to the same instant.  This function **does not** check this.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the MOD frame with the PEF frame.
