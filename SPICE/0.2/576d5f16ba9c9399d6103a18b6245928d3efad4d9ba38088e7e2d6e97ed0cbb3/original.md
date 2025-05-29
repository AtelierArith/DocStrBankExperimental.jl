```
surfpt(positn, u, a, b, c)
```

Determine the intersection of a line-of-sight vector with the surface of an ellipsoid.

### Arguments

  * `positn`: Position of the observer in body-fixed frame
  * `u`: Vector from the observer in some direction
  * `a`: Length of the ellipsoid semi-axis along the x-axis
  * `b`: Length of the ellipsoid semi-axis along the y-axis
  * `c`: Length of the ellipsoid semi-axis along the z-axis

### Output

Returns the point on the ellipsoid pointed to by u or `nothing` if none was found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/surfpt_c.html)
