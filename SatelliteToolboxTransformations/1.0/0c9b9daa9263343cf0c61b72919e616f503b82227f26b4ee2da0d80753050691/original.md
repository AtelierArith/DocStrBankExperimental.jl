```
cio_iau2006(jd_tt::Number) -> Float64, Float64, Float64
```

Compute the coordinates `X` and `Y` of the Celestial Intermediate Pole (CIP) with respect to the Geocentric Celestial Reference Frame (GCRF), and the CIO locator `s`. The algorithm is based on the IAU-2006 theory.

The CIO locator `s` provides the position of the CIO on the Equator of the CIP corresponding to the kinematical definition of the non-rotation origin in the GCRS when the CIP is moving with respect to the GCRS between the reference epoch and the epoch due to precession and nutation **[1]**(p. 214).

# Returns

  * `Float64`: The coordinate `X` of the CIP w.r.t. the GCRF.
  * `Float64`: The coordinate `Y` of the CIP w.r.t. the GCRF.
  * `Float64`: The CIO locator `s`.

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.  Microcosm   Press, Hawthorn, CA, USA.
