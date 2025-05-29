```
r_teme_to_tod([T, ]jd_tt::Number[, δΔϵ_1980::Number = 0, δΔψ_1980::Number = 0]) -> T
```

Compute the rotation that aligns the True Equator Mean Equinox (TEME) frame with the True of Date (TOD) frame at the Julian Day `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-76/FK5 theory and TEME definition in **[1]**(p. 233).  Notice that one can provide corrections for the nutation in obliquity (`δΔϵ_1980`) [rad] and in longitude (`δΔψ_1980`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref)).

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the TEME frame with the TOD frame.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
