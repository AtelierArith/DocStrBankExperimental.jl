```
spkw17(handle, body, center, frame, first, last, segid, epoch, eqel, rapol, decpol)
```

Write a type 17 segment to an SPK file.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `body`: Body code for ephemeris object
  * `center`: Body code for the center of motion of the body
  * `frame`: The reference frame of the states
  * `first`: First valid time for which states can be computed
  * `last`: Last valid time for which states can be computed
  * `segid`: Segment identifier
  * `epoch`: Epoch of elements in seconds past J2000
  * `eqel`: Array of equinoctial elements
  * `rapol`: Right Ascension of the pole of the reference plane
  * `decpol`: Declination of the pole of the reference plane

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw17_c.html)
