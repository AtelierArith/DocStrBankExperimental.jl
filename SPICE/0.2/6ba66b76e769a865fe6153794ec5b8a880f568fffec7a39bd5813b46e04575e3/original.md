```
recgeo(rectan, re, f)
```

Convert from rectangular coordinates to geodetic coordinates.

### Arguments

  * `rectan`: Rectangular coordinates of a point
  * `re`: Equatorial radius of the reference spheroid
  * `f`: Flattening coefficient

### Output

  * `lon`: Geodetic longitude of the point (radians)
  * `lat`: Geodetic latitude  of the point (radians)
  * `alt`: Altitude of the point above reference spheroid

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recgeo_c.html)
