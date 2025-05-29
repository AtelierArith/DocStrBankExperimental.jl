```
pckw02(handle, clssid, frame, first, last, segid, intlen, cdata, btime)
```

Write a type 2 segment to a PCK binary file given the file handle, frame class ID, base frame, time range covered by the segment, and the Chebyshev polynomial coefficients.

### Arguments

  * `handle`: Handle of binary PCK file open for writing.
  * `clssid`: Frame class ID of body-fixed frame.
  * `frame`: Name of base reference frame.
  * `first`: Start time of interval covered by segment.
  * `last`: End time of interval covered by segment.
  * `segid`: Segment identifier.
  * `intlen`: Length of time covered by logical record.
  * `cdata`: Array of Chebyshev coefficients.
  * `btime`: Begin time of first logical record.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pckw02_c.html)
