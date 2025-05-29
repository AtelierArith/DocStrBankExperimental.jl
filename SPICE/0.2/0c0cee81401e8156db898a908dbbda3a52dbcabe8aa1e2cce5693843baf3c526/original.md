```
ckw03(handle, begtim, endtim, inst, ref, segid, sclkdp, quats, starts, avvs=[zeros(3)])
```

Add a type 3 segment to a C-kernel.

### Arguments

  * `handle`: Handle of an open CK file
  * `begtim`: The beginning encoded SCLK of the segment
  * `endtim`: The ending encoded SCLK of the segment
  * `inst`: The NAIF instrument ID code
  * `ref`: The reference frame of the segment
  * `segid`: Segment identifier
  * `sclkdp`: Encoded SCLK times
  * `quats`: Quaternions representing instrument pointing
  * `starts`: Encoded SCLK interval start times
  * `avvs`: Angular velocity vectors (optional)

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw03_c.html)
