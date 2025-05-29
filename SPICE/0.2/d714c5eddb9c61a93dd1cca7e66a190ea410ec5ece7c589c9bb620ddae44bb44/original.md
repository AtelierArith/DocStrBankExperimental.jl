```
surfpv(stvrtx, stdir, a, b, c)
```

Find the state (position and velocity) of the surface intercept defined by a specified ray, ray velocity, and ellipsoid.

### Arguments

  * `stvrtx`: State of ray's vertex
  * `stdir`: State of ray's direction vector
  * `a`: Length of ellipsoid semi-axis along the x-axis
  * `b`: Length of ellipsoid semi-axis along the y-axis
  * `c`: Length of ellipsoid semi-axis along the z-axis

### Output

Return the state of surface intercept or `nothing` if none was found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/surfpv_c.html)
