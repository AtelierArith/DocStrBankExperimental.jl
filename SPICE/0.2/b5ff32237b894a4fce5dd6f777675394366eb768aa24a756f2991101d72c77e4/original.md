```
pgrrec(body, lon, lat, alt, re, f)
```

Convert planetographic coordinates to rectangular coordinates.

### Arguments

  * `body`: Body with which coordinate system is associated.
  * `lon`: Planetographic longitude of a point (radians).
  * `lat`: Planetographic latitude of a point (radians).
  * `alt`: Altitude of a point above reference spheroid.
  * `re`: Equatorial radius of the reference spheroid.
  * `f`: Flattening coefficient.

### Output

Returns the rectangular coordinates of the point.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pgrrec_c.html)
