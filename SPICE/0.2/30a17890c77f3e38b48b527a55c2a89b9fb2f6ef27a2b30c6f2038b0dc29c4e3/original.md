```
drdlat(radius, lon, lat)
```

Compute the Jacobian of the transformation from latitudinal to rectangular coordinates.

### Arguments

  * `radius`: Distance of a point from the origin
  * `lon`: Angle of the point from the XZ plane in radians
  * `lat`: Angle of the point from the XY plane in radians

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdlat_c.html)
