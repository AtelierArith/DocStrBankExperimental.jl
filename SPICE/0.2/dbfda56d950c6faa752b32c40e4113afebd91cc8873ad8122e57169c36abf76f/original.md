```
spkw02(handle, body, center, frame, first, last, segid, intlen, cdata, btime)
```

Write a type 2 segment to an SPK file.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `body`: Body code for ephemeris object
  * `center`: Body code for the center of motion of the body
  * `frame`: The reference frame of the states
  * `first`: First valid time for which states can be computed
  * `last`: Last valid time for which states can be computed
  * `segid`: Segment identifier
  * `intlen`: Length of time covered by logical record
  * `cdata`: Array of Chebyshev coefficients
  * `btime`: Begin time of first logical record

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw02_c.html)
