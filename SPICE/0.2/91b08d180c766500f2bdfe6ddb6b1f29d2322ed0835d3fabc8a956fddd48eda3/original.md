```
dskx02(handle, dladsc, vertex, raydir)
```

Determine the plate ID and body-fixed coordinates of the intersection of a specified ray with the surface defined by a type 2 DSK plate model.

### Arguments

  * `handle`: Handle of DSK kernel containing plate model
  * `dladsc`: DLA descriptor of plate model segment
  * `vertex`: Ray vertex in the body fixed frame
  * `raydir`: Ray direction in the body fixed frame

### Output

Returns `nothing` if no intercept exists or

  * `plid`: ID code of the plate intersected by the ray
  * `xpt`: Intercept

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskx02_c.html)
