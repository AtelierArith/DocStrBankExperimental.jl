```
spkw12(handle, body, center, frame, first, last, segid, degree, states, epoch1, step)
```

Write a type 12 segment to an SPK file.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `body`: Body code for ephemeris object
  * `center`: Body code for the center of motion of the body
  * `frame`: The reference frame of the states
  * `first`: First valid time for which states can be computed
  * `last`: Last valid time for which states can be computed
  * `segid`: Segment identifier
  * `degree`: Degree of interpolating polynomials
  * `states`: States
  * `epoch1`: Epoch of first state in states array
  * `step`: Time step separating epochs of states

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw12_c.html)
