```
r_ers_to_tirs_iau2006(jd_ut1::Number, jd_tt::Number, δΔΨ_2000::Number = 0) -> T
```

Compute the rotation that aligns the Earth Reference System (ERS) with the Terrestrial Intermediate Reference System (TIRS) at the Julian Day `jd_ut1` [UT1] and `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-2006 theory.

Notice that one can provide corrections for the nutation in longitude (`δΔψ_2000`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref) and [`compute_δΔϵ_δΔψ`](@ref)). This corrections are related to Free Core Nutation (FCN) that models the effect of a liquid Earth core.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the ERS frame with the TIRS frame.

# Remarks

The reference frames TIRS and ERS are separated by a rotation about the Z-axis of the Greenwhich apparent sidereal angle (GAST). This angle is computed using the IAU-2006 theory, which consist of obtaining the Earth Rotation Angle (ERA) and subtracting the result of the Equation of Origins (EO).
