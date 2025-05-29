```
dpgrdr(x, y, z, re, f)
```

Compute the Jacobian of the transformation from rectangular to planetographic coordinates.

### Arguments

  * `body`: Body with which coordinate system is associated
  * `x`: X-coordinate of point
  * `y`: Y-coordinate of point
  * `z`: Z-coordinate of point
  * `re`: Equatorial radius of the reference spheroid
  * `f`: Flattening coefficient

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dpgrdr_c.html)
