```
dazldr(x, y, z; azccw=true, elplsz=true)
```

Compute the Jacobian matrix of the transformation from rectangular to azimuth/elevation coordinates.

### Arguments

  * `x`: X-coordinate of point
  * `y`: Y-coordinate of point
  * `z`: Z-coordinate of point

### Keyword Arguments

  * `azccw`: Flag indicating how azimuth is measured. If `true` (the default), the azimuth increases in the counterclockwise direction; otherwise it increases in the clockwise direction
  * `elplsz`: Flag indicating how elevation is measured. If `true` (the default), the elevation increases from the XY plane toward +Z; otherwise toward -Z

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dazldr_c.html)
