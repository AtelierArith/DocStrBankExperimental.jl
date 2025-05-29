```
recpgr(body, rectan, re, f)
```

Convert rectangular coordinates to planetographic coordinates.

### Arguments

  * `body`: Body with which coordinate system is associated
  * `rectan`: Rectangular coordinates of a point
  * `re`: Equatorial radius of the reference spheroid
  * `f`: flattening coefficient

### Output

  * `lon`: Planetographic longitude of the point (radians).
  * `lat`: Planetographic latitude of the point (radians).
  * `alt`: Altitude of the point above reference spheroid.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recpgr_c.html)
