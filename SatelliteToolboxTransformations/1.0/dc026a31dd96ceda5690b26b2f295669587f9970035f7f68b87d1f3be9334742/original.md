```
r_tirs_to_mod_iau2006([T, ]jd_ut1::Number, jd_tt::Number, δΔϵ_2000::Number = 0, δΔΨ_2000::Number = 0) -> T
```

Compute the rotation that aligns the Terrestrial Intermediate Reference System (TIRS) with the Mean of Date (MOD) reference frame at the Julian Day `jd_ut1` [UT1] and `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-2006 theory.

Notice that one can provide corrections for the nutation in obliquity (`δΔϵ_2000`) and in longitude (`δΔψ_2000`) [rad] that are usually obtained from IERS EOP Data (see [`fetch_iers_eop`](@ref) and [`compute_δΔϵ_δΔψ`](@ref)).  This corrections are related to Free Core Nutation (FCN) that models the effect of a liquid Earth core.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

!!! info
    This composed rotation TIRS <=> ERS <=> MOD is implemented as a new function because the single rotations TIRS <=> ERS and ERS <=> MOD call the function `nutation_eo`, which has a high computational burden. In this case, the composed algorithm is about 2x faster than calling those function separately.


# Returns

  * `T`: The rotation that aligns the TIRS frame with the ERS frame.
