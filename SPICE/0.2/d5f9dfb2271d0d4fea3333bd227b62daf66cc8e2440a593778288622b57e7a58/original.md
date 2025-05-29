```
frame(x)
```

Given a vector `x`, this routine builds a right handed orthonormal frame `x`, `y`, `z` where the output `x` is parallel to the input `x`.

### Arguments

  * `x`: Input vector

### Output

  * `x`: Unit vector parallel to `x` on output
  * `y`: Unit vector in the plane orthogonal to `x`
  * `z`: Unit vector given by `x × y`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/frame_c.html)
