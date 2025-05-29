```
lgrind(xvals, yvals, x)
```

Evaluate a Lagrange interpolating polynomial for a specified set of coordinate pairs, at a specified abscissa value. Return the value of both polynomial and derivative.

### Arguments

  * `xvals`: Abscissa values of coordinate pairs
  * `yvals`: Ordinate values of coordinate pairs
  * `x`: Point at which to interpolate the polynomial

### Output

  * `p`: The value at x of the unique polynomial of      degree n-1 that fits the points in the plane      defined by xvals and yvals
  * `dp`: The derivative at x of the interpolating       polynomial described above

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lgrind_c.html)
