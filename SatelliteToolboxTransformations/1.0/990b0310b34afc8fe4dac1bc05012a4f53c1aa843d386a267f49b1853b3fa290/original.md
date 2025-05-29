```
r_tod_to_pef_fk5([T, ]jd_ut1::Number, jd_tt::Number[, δΔψ_1980::Number]) -> T
```

Compute the rotation that aligns the True of Date (TOD) frame with the Pseudo-Earth Fixed (PEF) frame at the Julian Day `jd_ut1` [UT1] and `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-76/FK5 theory. Notice that one can provide correction for the nutation in longitude (`δΔψ_1980`) [rad] that is usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

The Julian Day in UT1 is used to compute the Greenwich Mean Sidereal Time (GMST) (see `jd_to_gmst`), whereas the Julian Day in Terrestrial Time is used to compute the nutation in the longitude. Notice that the Julian Day in UT1 and in Terrestrial Time must be equivalent, i.e. must be related to the same instant.  This function **does not** check this.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the TOD frame with the PEF frame.

# Remarks

The True of Date (TOD) frame is rotated into the Pseudo-Earth Fixed (PEF) frame considering the 1980 IAU Theory of Nutation. The IERS EOP corrections must be added if one wants to make the rotation consistent with the Geocentric Celestial Reference Systems (GCRS).
