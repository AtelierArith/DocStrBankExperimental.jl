```
qdq2av(q, dq)
```

Derive angular velocity from a unit quaternion and its derivative with respect to time.

### Arguments

  * `q`: Unit SPICE quaternion (as any kind of iterable with four elements)
  * `dq`: Derivative of `q` with respect to time

### Output

Angular velocity vector defined by `q` and `dq`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/qdq2av_c.html)
