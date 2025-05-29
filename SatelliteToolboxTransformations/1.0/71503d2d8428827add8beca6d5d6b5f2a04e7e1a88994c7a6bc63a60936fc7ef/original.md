```
r_itrf_to_gcrf_fk5([T, ]jd_ut1::Number, jd_tt::Number, x_p::Number, y_p::Number[, δΔϵ_1980::Number, δΔψ_1980::Number]) -> T
```

Compute the rotation that aligns the International Terrestrial Reference Frame (ITRF) with the Geocentric Celestial Reference Frame (GCRF) at the Julian Day `jd_ut1` [UT1] and `jd_tt` [Terrestrial Time], and considering the IERS EOP Data `x_p` [rad], `y_p` [rad], `δΔϵ_1980` [rad], and `δΔψ_1980` [rad] (see [`fetch_iers_eop`](@ref)). This algorithm uses the IAU-76/FK5 theory.

`x_p` is the polar motion displacement about X-axis, which is the IERS Reference Meridian direction (positive south along the 0˚ longitude meridian). `y_p` is the polar motion displacement about Y-axis (90˚W or 270˚E meridian). `δΔϵ_1980` is the nutation in obliquity. `δΔψ_1980` is the nutation in longitude.

The Julian Day in UT1 is used to compute the Greenwich Mean Sidereal Time (GMST) (see `jd_to_gmst`), whereas the Julian Day in Terrestrial Time is used to compute the nutation in the longitude. Notice that the Julian Day in UT1 and in Terrestrial Time must be equivalent, i.e. must be related to the same instant.  This function **does not** check this.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the ITRF frame with the GCRF frame.

# Remarks

The EOP data related to the polar motion (`x_p` and `y_p`) is required, since this is the only way available to compute the conversion ITRF <=> PEF (the models are highly imprecise since the motion is still not very well understood **[1]**). However, the EOP data related to the nutation of the obliquity (`δΔϵ_1980`) and the nutation of the longitude (`δΔψ_1980`) can be omitted. In this case, the GCRF frame is what is usually called J2000 reference frame.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.  Microcosm   Press, Hawthorn, CA, USA.
