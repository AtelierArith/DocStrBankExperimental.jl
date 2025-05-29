```
tipbod(ref, body, et)
```

Return a 3×3 matrix that transforms positions in inertial coordinates to positions in body-equator-and-prime-meridian coordinates.

### Arguments

  * `ref`: Name of inertial reference frame to transform from
  * `body`: ID code of body
  * `et`: Epoch of transformation

### Output

Returns transformation matrix from intertial position to prime meridian.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/tipbod_c.html)
