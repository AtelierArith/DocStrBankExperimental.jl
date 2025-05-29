```
ilumin(method, target, et, fixref, obsrvr, spoint, abcorr)
```

Find the illumination angles (phase, solar incidence, and emission) at a specified surface point of a target body.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in ephemeris seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `obsrvr`: Name of observing body
  * `spoint`: Body-fixed coordinates of a target surface point
  * `abcorr`: Aberration correction

### Output

  * `trgepc`: Sub-solar point epoch
  * `srfvec`: Vector from observer to sub-solar point
  * `phase`: Phase angle at the surface point
  * `incdnc`: Solar incidence angle at the surface point
  * `emissn`: Emission angle at the surface point

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ilumin_c.html)
