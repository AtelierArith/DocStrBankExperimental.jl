```
sphcyl(radius, colat, slon)
```

Converts from spherical coordinates to cylindrical coordinates.

### Arguments

  * `radius`: Distance of point from origin
  * `colat`: Polar angle (co-latitude in radians) of point
  * `slon`: Azimuthal angle (longitude) of point (radians)

### Output

  * `r`: Distance of point from Z axis
  * `lon`: Angle (radians) of point from XZ plane
  * `z`: Height of point above XY plane

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sphcyl_c.html)
