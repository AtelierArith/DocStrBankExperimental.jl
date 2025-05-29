```
spkpds(body, center, frame, typ, first, last)
```

Perform routine error checks and if all checks pass, pack the descriptor for an SPK segment.

### Arguments

  * `body`: The NAIF ID code for the body of the segment
  * `center`: The center of motion for body
  * `frame`: The frame for this segment
  * `type`: The type of SPK segment to create
  * `first`: The first epoch for which the segment is valid
  * `last`: The last  epoch for which the segment is valid

### Output

Returns an SPK segment descriptor.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpds_c.html)
