```
tisbod(ref, body, et)
```

Return a 6×6 matrix that transforms states in inertial coordinates to states in body-equator-and-prime-meridian coordinates.

### Arguments

  * `ref`: Name of inertial reference frame to transform from
  * `body`: ID code of body
  * `et`: Epoch of transformation

### Output

Returns transformation matrix from intertial state to prime meridian.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/tisbod_c.html)
