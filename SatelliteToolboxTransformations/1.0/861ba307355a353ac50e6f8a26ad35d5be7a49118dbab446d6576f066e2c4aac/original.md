```
r_mod_to_gcrf_fk5([T, ]jd_tt::Number) -> T
```

Compute the rotation that aligns the Mean of Date (MOD) frame with the Geocentric Celestial Reference Frame (GCRF) at the Julian Day [Terrestrial Time] `jd_tt`. This algorithm uses the IAU-76/FK5 theory.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the MOD frame with the GCRF frame.

# Remarks

The Mean of Date (MOD) frame is rotated into the Geocentric Celestial Reference Frame (GCRF) considering the IAU 1976 Precession model.

Notice that if the conversion `TOD => MOD` is performed **without** considering the EOP corrections, then the GCRF obtained by this rotation is what is usually called the J2000 reference frame.
