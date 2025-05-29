```
pxfrm2(from, to, etfrom, etto)
```

Return the 3×3 matrix that transforms position vectors from one specified frame at a specified epoch to another specified frame at another specified epoch.

### Arguments

  * `from`: Name of the frame to transform from
  * `to`: Name of the frame to transform to
  * `etfrom`: Evaluation time of `from` frame
  * `etto`: Evaluation time of `to` frame

### Output

Returns a position transformation matrix from frame `from` to frame `to`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pxfrm2_c.html)
