```
drdpgr(body, lon, lat, alt, re, f)
```

Compute the Jacobian matrix of the transformation from planetographic to rectangular coordinates.

### Arguments

  * `body`: Name of body with which coordinates are associated
  * `lon`: Planetographic longitude of a point (radians)
  * `lat`: Planetographic latitude of a point (radians)
  * `alt`: Altitude of a point above reference spheroid
  * `re`: Equatorial radius of the reference spheroid
  * `f`: Flattening coefficient

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdpgr_c.html)
