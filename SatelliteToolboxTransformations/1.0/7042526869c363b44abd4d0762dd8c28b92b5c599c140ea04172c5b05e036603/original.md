```
r_gcrf_to_cirs_iau2006([T, ]jd_tt::Number, δx::Number = 0, δy::Number = 0) -> T
```

Compute the rotation that aligns the Geocentric Celestial Reference Frame (GCRF) with the Celestial Intermediate Reference System (CIRS) at the Julian Day `jd_tt` [TT] and considering the IERS EOP Data `δx` [rad] and `δy` [rad] (see [`fetch_iers_eop`](@ref)). This algorithm uses the IAU-2006 theory.

The IERS EOP Data `δx` and `δy` accounts for the free-core nutation and time dependent effects of the Celestial Intermediate Pole (CIP) position with respect to the GCRF.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the GCRF frame with the CIRS frame.
