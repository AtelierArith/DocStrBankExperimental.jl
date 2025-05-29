```
r_pef_to_teme([T, ]jd_tt::Number) -> T
```

Compute the rotation that aligns the Pseudo-Earth Fixed (PEF) frame with the True Equator Mean Equinox (TEME) frame at the Julian Day `jd_tt` [Terrestrial Time]. This algorithm uses the IAU-76/FK5 theory and TEME definition in **[1]**(p. 233).

The rotation type is described by the optional variable `T`. If it is `DCM`, then a DCM will be returned. Otherwise, if it is `Quaternion`, then a Quaternion will be returned. In case this parameter is omitted, then it falls back to `DCM`.

# Returns

  * `T`: The rotation that aligns the PEF frame with the TEME frame.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
