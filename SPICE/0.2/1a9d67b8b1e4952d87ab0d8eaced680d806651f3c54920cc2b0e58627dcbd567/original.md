```
spkw20(handle, body, center, frame, first, last, segid, intlen, n, polydg, cdata, dscale,
       tscale, initjd, initfr)
```

Write a type 20 segment to an SPK file.

### Arguments

  * `handle`: Handle of SPK file open for writing
  * `body`: NAIF code for ephemeris object
  * `center`: NAIF code for the center of motion of the body
  * `frame`: Reference frame name
  * `first`: Start time of interval covered by segment
  * `last`: End time of interval covered by segment
  * `segid`: Segment identifier
  * `intlen`: Length of time covered by logical record (days)
  * `cdata`: Array of Chebyshev coefficients and positions
  * `dscale`: Distance scale of data
  * `tscale`: Time scale of data
  * `initjd`: Integer part of begin time (TDB Julian date) of first record
  * `initfr`: Fractional part of begin time (TDB Julian date) of first record

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw20_c.html)
