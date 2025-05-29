```
nplnpt(linept, linedr, point)
```

Find the nearest point on a line to a specified point, and find the distance between the two points.

### Arguments

  * `linept`: Point on line
  * `linedr`: Direction vector of line
  * `point`: A second point

### Output

Returns a tuple consisting of `pnear` and `dist`.

  * `pnear`: Nearest point on the line to `point`
  * `dist`: Distance between `point` and `pnear`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/nplnpt_c.html)
