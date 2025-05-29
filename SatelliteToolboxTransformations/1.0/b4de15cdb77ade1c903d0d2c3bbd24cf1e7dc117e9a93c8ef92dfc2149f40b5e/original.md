```
precession_iau2006(jd_tt::Number) -> NTuple{3, Float64}
```

Compute the precession angles [rad] according to equinox-based IAU-2006 theory in the Julia day `jd_tt` [Terrestrial Time].

This algorithm was obtained from **[1]**(p. 49).

# References

  * **[1]**: IERS (2010). Transformation between the International Terrestrial Reference   System and the Geocentric Celestial Reference System. IERS Technical Note No. 36,   Chapter 5.
