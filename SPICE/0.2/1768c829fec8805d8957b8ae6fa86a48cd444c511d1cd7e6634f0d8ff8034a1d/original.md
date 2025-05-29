```
ckw05(handle, subtyp, degree, begtim, endtim, inst, ref, avflag, segid, sclkdp, packts,
      rate, nints, starts)
```

Write a type 5 segment to a CK file.

### Arguments

  * `handle`: Handle of an open CK file
  * `subtyp`: CK type 5 subtype code
  * `degree`: Degree of interpolating polynomials
  * `begtim`: The beginning encoded SCLK of the segment
  * `endtim`: The ending encoded SCLK of the segment
  * `inst`: The NAIF instrument ID code
  * `ref`: The reference frame of the segment
  * `avflag`: True if the segment will contain angular velocity
  * `segid`: Segment identifier
  * `sclkdp`: Encoded SCLK times
  * `packts`: Array of packets
  * `rate`: Nominal SCLK rate in seconds per tick
  * `nints`: Number of intervals
  * `starts`: Encoded SCLK interval start times

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckw05_c.html)
