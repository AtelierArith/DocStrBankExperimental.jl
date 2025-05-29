```
spkw10(handle, body, center, frame, first, last, segid, consts, elems, epochs)
```

Write a type 10 segment to an SPK file.

### Arguments

  * `handle`: The handle of a DAF file open for writing
  * `body`: The NAIF ID code for the body of the segment
  * `center`: The center of motion for body
  * `frame`: The reference frame for this segment
  * `first`: The first epoch for which the segment is valid
  * `last`: The last  epoch for which the segment is valid
  * `segid`: The string to use for segment identifier
  * `consts`: The array of geophysical constants for the segmen
  * `elems`: The collection of "two-line" element sets
  * `epochs`: The epochs associated with the element sets

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw10_c.html)
