```
drdazl(range, az, el; azccw=true, elplsz=true)
```

Compute the Jacobian matrix of the transformation from azimuth/elevation to rectangular coordinates.

### Arguments

  * `range`: Distance of a point from the origin
  * `az`: Azimuth of input point in radians
  * `el`: Elevation of input point in radians

### Keyword Arguments

  * `azccw`: Flag indicating how azimuth is measured. If `true` (the default), the azimuth increases in the counterclockwise direction; otherwise it increases in the clockwise direction
  * `elplsz`: Flag indicating how elevation is measured. If `true` (the default), the elevation increases from the XY plane toward +Z; otherwise toward -Z

### Output

Returns the matrix of partial derivatives.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/drdazl_c.html)
