```
nearpt(positn, a, b, c)
```

This routine locates the point on the surface of an ellipsoid that is nearest to a specified position. It also returns the altitude of the position above the ellipsoid.

### Arguments

  * `positn`: Position of a point in the bodyfixed frame
  * `a`: Length of semi-axis parallel to x-axis
  * `b`: Length of semi-axis parallel to y-axis
  * `c`: Length on semi-axis parallel to z-axis

### Output

Returns a tuple consisting of `npoint` and `alt`.

  * `npoint`: Point on the ellipsoid closest to `positn`
  * `alt`: Altitude of `positn` above the ellipsoid

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/nearpt_c.html)
