```
npelpt(point, ellips)
```

Find the nearest point on an ellipse to a specified point, both in three-dimensional space, and find the distance between the ellipse and the point.

### Arguments

  * `point`: Point whose distance to an ellipse is to be found
  * `ellips`: A SPICE ellipse

### Output

Returns a tuple consisting of `pnear` and `dist`.

  * `pnear`: Nearest point on ellipse to input point
  * `dist`: Distance of input point to ellipse

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/npelpt_c.html)
