```
spkw15(handle, body, center, frame, first, last, segid,
       epoch, tp, pa, p, ecc, j2flg, pv, gm, j2, radius)
```

Write a type 15 segment to an SPK file.

### Arguments

  * `handle`: Handle of an SPK file open for writing
  * `body`: Body code for ephemeris object
  * `center`: Body code for the center of motion of the body
  * `frame`: The reference frame of the states
  * `first`: First valid time for which states can be computed
  * `last`: Last valid time for which states can be computed
  * `segid`: Segment identifier
  * `epoch`: Epoch of the periapse
  * `tp`: Trajectory pole vector
  * `pa`: Periapsis vector
  * `p`: Semi-latus rectum
  * `ecc`: Eccentricity
  * `j2flg`: J2 processing flag
  * `pv`: Central body pole vector
  * `gm`: Central body GM
  * `j2`: Central body J2
  * `radius`: Equatorial radius of central body

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw15_c.html)
