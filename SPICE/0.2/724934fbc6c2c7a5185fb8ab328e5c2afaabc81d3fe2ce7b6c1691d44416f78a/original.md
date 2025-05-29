```
latsph(radius, lon, lat)
```

Convert from latitudinal coordinates to spherical coordinates.

### Arguments

  * `radius`: Distance of a point from the origin
  * `lon`: Angle of the point from the XZ plane in radians
  * `lat`: Angle of the point from the XY plane in radians

### Output

Return the tuple `(rho, colat, lons)`.

  * `rho`: Distance of the point from the origin
  * `colat`: Angle of the point from positive z axis (radians)
  * `lons`: Angle of the point from the XZ plane (radians)

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latsph_c.html)
