```
drdsph(r, colat, lon)
```

Compute the Jacobian of the transformation from latitudinal to rectangular coordinates.

### Arguments

  * `r`: Distance of a point from the origin
  * `colat`: Angle of the point from the positive z-axis
  * `lon`: Angle of the point from the xy plane

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdsph_c.html)
