```
drdgeo(lon, lat, alt, re, f)
```

Compute the Jacobian of the transformation from geodetic to rectangular coordinates.

### Arguments

  * `lon`: Geodetic longitude of point (radians)
  * `lat`: Geodetic latitude of point (radians)
  * `alt`: Altitude of point above the reference spheroid
  * `re`: Equatorial radius of the reference spheroid
  * `f`: Flattening coefficient

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdgeo_c.html)
