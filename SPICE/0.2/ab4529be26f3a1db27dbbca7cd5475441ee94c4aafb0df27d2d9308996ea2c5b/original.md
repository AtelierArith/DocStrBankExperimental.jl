```
recazl(rectan; azccw=true, elplsz=true)
```

Convert rectangular coordinates of a point to range, azimuth and elevation.

### Arguments

  * `rectan`: Rectangular coordinates of a point

### Keyword Arguments

  * `azccw`: Flag indicating how azimuth is measured. If `true` (the default), the azimuth increases in the counterclockwise direction; otherwise it increases in the clockwise direction
  * `elplsz`: Flag indicating how elevation is measured. If `true` (the default), the elevation increases from the XY plane toward +Z; otherwise toward -Z

### Output

Returns a tuple consisting of:

  * `range`: Distance of the point from the origin
  * `az`: Azimuth in radians
  * `el`: Elevation in radians

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/recazl_c.html)
