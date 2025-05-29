```
pltnp(point, v1, v2, v3)
```

Find the nearest point on a triangular plate to a given point.

### Arguments

  * `point`: A point in 3-dimensional space.
  * `v1`, `v2`, `v3`: Vertices of a triangular plate

### Output

Returns a tuple consisting of

  * `pnear`: Nearest point on the plate to `point`
  * `dist`: Distance between `pnear` and `point`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pltnp_c.html)
