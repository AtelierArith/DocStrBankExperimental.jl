```
spkw18(handle, subtyp, body, center, frame, first, last, segid, degree, packts, epochs)
```

Write a type 18 segment to an SPK file.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `subtyp`: SPK type 18 subtype code, either `:S18TP0` or `:S18TP1`
  * `body`: NAIF code for an ephemeris object
  * `center`: NAIF code for center of motion of body
  * `frame`: Reference frame name
  * `first`: Start time of interval covered by segment
  * `last`: End time of interval covered by segment
  * `segid`: Segment identifier
  * `degree`: Degree of interpolating polynomials
  * `packts`: Time-ordered array of data packets representing geometric states of body

      * For `:S18TP0`: `[x,  y,  z,  dx/dt,  dy/dt,  dz/dt, vx, vy, vz, dvx/dt, dvy/dt, dvz/dt]`
      * For `:S18TP1`: `[x,  y,  z,  dx/dt,  dy/dt,  dz/dt]`
  * `epochs`: Array of epochs corresponding to states.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw18_c.html)
