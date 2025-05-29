```
georec(lon, lat, alt, re, f)
```

Convert geodetic coordinates to rectangular coordinates.

### Arguments

  * `lon`: Geodetic longitude of point (radians)
  * `lat`: Geodetic latitude  of point (radians)
  * `alt`: Altitude of point above the reference spheroid
  * `re`: Equatorial radius of the reference spheroid
  * `f`: Flattening coefficient

### Output

Returns the rectangular coordinates of point.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/georec_c.html)
