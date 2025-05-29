```
r_cirs_to_tirs_iau2006([T, ]jd_ut1::Number) -> T
```

Compute the rotation that aligns the Celestial Intermediate Reference System (CIRS) with the Terrestrial Intermediate Reference System (TIRS) at the Julian Day `jd_ut1` [UT1]. This algorithm uses the IAU-2006 theory.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

The rotation that aligns the CIRS frame with the TIRS frame. The rotation representation is selected by the optional parameter `T`.

# Remarks

The reference frames TIRS and CIRS are separated by a rotation about the Z-axis of the Earth Rotation Angle, which is the angle between the Conventional International Origin (CIO) and the Terrestrial Intermediate Origin (TIO) **[1]**. The latter is a reference meridian on Earth that is located about 100m away from Greenwich meridian along the equator of the Celestial Intermediate Pole (CIP) **[1]**.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.  Microcosm   Press, Hawthorn, CA, USA.
