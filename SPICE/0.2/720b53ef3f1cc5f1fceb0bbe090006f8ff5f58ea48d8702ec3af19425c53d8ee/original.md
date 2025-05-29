```
illumg(method, target, ilusrc, et, fixref, obsrvr, spoint, abcorr)
```

Find the illumination angles (phase, incidence, and emission) at a specified surface point of a target body.

The surface of the target body may be represented by a triaxial ellipsoid or by topographic data provided by DSK files.

The illumination source is a specified ephemeris object.

### Arguments

  * `method`: Computation method.
  * `target`: Name of target body.
  * `ilusrc`: Name of illumination source.
  * `et`: Epoch in ephemeris seconds past J2000 TDB.
  * `fixref`: Body-fixed, body-centered target body frame.
  * `obsrvr`: Name of observing body.
  * `spoint`: Body-fixed coordinates of a target surface point.
  * `abcorr`: Aberration correction.

### Output

  * `trgepc`: Sub-solar point epoch.
  * `srfvec`: Vector from observer to sub-solar point.
  * `phase`: Phase angle at the surface point.
  * `incdnc`: Solar incidence angle at the surface point.
  * `emissn`: Emission angle at the surface point.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/illumg_c.html)
