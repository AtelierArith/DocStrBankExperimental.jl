```
drdcyl(r, lon, z)
```

Compute the Jacobian of the transformation from cylindrical to rectangular coordinates.

### Arguments

  * `r`: Distance of a point from the origin
  * `lon`: Angle of the point from the xz plane in radians
  * `z`: Height of the point above the xy plane

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdcyl_c.html)
