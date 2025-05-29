```
latcyl(radius, lon, lat)
```

Convert from latitudinal coordinates to cylindrical coordinates.

### Arguments

  * `radius`: Distance of a point from the origin
  * `lon`: Angle of the point from the XZ plane in radians
  * `lat`: Angle of the point from the XY plane in radians

### Output

Return the tuple `(r, lonc, z)`.

  * `r`: Distance of the point from the z axis
  * `lonc`: Angle of the point from the XZ plane in radians. 'lonc' is set equal to 'lon'
  * `z`: Height of the point above the XY plane

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latcyl_c.html)
