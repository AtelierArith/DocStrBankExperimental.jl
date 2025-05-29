```
npedln(a, b, c, linept, linedr)
```

Find nearest point on a triaxial ellipsoid to a specified line, and the distance from the ellipsoid to the line.

### Arguments

  * `a`: Length of semi-axis in the x direction
  * `b`: Length of semi-axis in the y direction
  * `c`: Length of semi-axis in the z direction
  * `linept`: Point on line
  * `linedr`: Direction vector of line

### Output

Returns a tuple consisting of `pnear` and `dist`.

  * `pnear`: Nearest point on ellipsoid to line
  * `dist`: Distance of ellipsoid from line

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/npedln_c.html)
