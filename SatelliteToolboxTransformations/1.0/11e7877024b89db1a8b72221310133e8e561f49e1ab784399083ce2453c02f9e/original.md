```
r_gcrf_to_mj2000_iau2006([T, ]jd_tt::Number = 0) -> T
```

Compute the rotation that aligns the Geocentric Celestial Reference Frame (GCRF) with the J2000 mean equatorial frame. This algorithm uses the IAU-2006 theory.  Notice that this rotation is just a bias matrix that does not depend on the date. However, this function receives the argument `jd_tt` just to keep the API compatibility.

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

!!! info
    According to **[1]**, the frame bias that converts MJ2000 <=> GCRF is not a precise transformation for all the times.


# Returns

  * `T`: The rotation that aligns the MJ2000 frame with the MOD frame.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
