```
cylsph(r, lonc, z)
```

Convert from cylindrical to spherical coordinates.

### Arguments

  * `r`: Distance of point from z axis
  * `lonc`: Angle (radians) of point from XZ plane
  * `z`: Height of point above XY plane

### Output

  * `radius`: Distance of the point from the origin
  * `colat`: Polar angle (co-latitude in radians)
  * `lon`: Azimuthal angle (longitude)

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/cylsph_c.html)
