```
azlrec(range, az, el; azccw=true, elplsz=true)
```

Convert from range, azimuth and elevation of a point to rectangular coordinates.

### Arguments

  * `range`: Distance of the point from the origin
  * `az`: Azimuth in radians
  * `el`: Elevation in radians

### Keyword Arguments

  * `azccw`: Flag indicating how azimuth is measured. If `true` (the default), the azimuth increases in the counterclockwise direction; otherwise it increases in the clockwise direction
  * `elplsz`: Flag indicating how elevation is measured. If `true` (the default), the elevation increases from the XY plane toward +Z; otherwise toward -Z

### Output

  * `rectan`: Rectangular coordinates of the point

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/azlrec_c.html)
