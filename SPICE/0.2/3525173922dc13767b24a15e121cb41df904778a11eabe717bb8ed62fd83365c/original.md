```
ckw02(handle, begtim, endtim, inst, ref, segid, start, stop, quats, avvs, rates)
```

Write a type 2 segment to a C-kernel.

### Arguments

  * `handle`: Handle of an open CK file
  * `begtim`: The beginning encoded SCLK of the segment
  * `endtim`: The ending encoded SCLK of the segment
  * `inst`: The NAIF instrument ID code
  * `ref`: The reference frame of the segment
  * `segid`: Segment identifier
  * `start`: Encoded SCLK interval start times
  * `stop`: Encoded SCLK interval stop times
  * `quats`: Quaternions representing instrument pointing
  * `avvs`: Angular velocity vectors
  * `rates`: Number of seconds per tick for each interval

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw02_c.html)
