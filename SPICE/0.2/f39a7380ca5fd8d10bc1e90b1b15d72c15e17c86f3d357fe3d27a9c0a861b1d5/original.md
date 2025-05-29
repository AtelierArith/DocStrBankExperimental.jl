```
spkw05(handle, body, center, frame, first, last, segid, gm, states, epochs)
```

Write an SPK segment of type 5 given a time-ordered set of discrete states and epochs, and the gravitational parameter of a central body.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `body`: Body code for ephemeris object
  * `center`: Body code for the center of motion of the body
  * `frame`: The reference frame of the states
  * `first`: First valid time for which states can be computed
  * `last`: Last valid time for which states can be computed
  * `segid`: Segment identifier
  * `gm`: Gravitational parameter of central body
  * `states`: States
  * `epochs`: Epochs

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw05_c.html)
