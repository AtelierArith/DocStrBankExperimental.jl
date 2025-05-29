```
subpnt(method, target, et, fixref, obsrvr, abcorr)
```

Compute the rectangular coordinates of the sub-observer point on a target body at a specified epoch, optionally corrected for light time and stellar aberration.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in ephemeris seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction
  * `obsrvr`: Name of observing body

### Output

  * `spoint`: Sub-solar point on the target body
  * `trgepc`: Sub-solar point epoch
  * `srfvec`: Vector from observer to sub-solar point

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/subpnt_c.html)
