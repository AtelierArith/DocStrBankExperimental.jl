```
r_gcrf_to_mod_fk5([T, ]jd_tt::Number) -> T
```

Compute the rotation that aligns the Geocentric Celestial Reference Frame (GCRF) with the Mean of Date (MOD) frame at the Julian Day [Terrestrial Time] `jd_tt`.  This algorithm uses the IAU-76/FK5 theory.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the GCRF frame with the MOD frame.

# Remarks

The Geocentric Celestial Reference Frame (GCRF) is rotated into the Mean of Date (MOD) frame considering the IAU 1976 Precession model.

Notice that if the conversion `MOD => TOD` is performed **without** considering the EOP corrections, then the GCRF in this rotation is what is usually called the J2000 reference frame.
