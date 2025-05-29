```
sincpt(method, target, et, fixref, abcorr, obsrvr, dref, dvec)
```

Given an observer and a direction vector defining a ray, compute the surface intercept of the ray on a target body at a specified epoch, optionally corrected for light time and stellar aberration.

The surface of the target body may be represented by a triaxial ellipsoid or by topographic data provided by DSK files.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in TDB seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of observing body
  * `dref`: Reference frame of ray's direction vector
  * `dvec`: Ray's direction vector

### Output

Returns a tuple consisting of the following data or `nothing` if no intercept was found.

  * `spoint`: Surface intercept point on the target body
  * `trgepc`: Intercept epoch
  * `srfvec`: Vector from observer to intercept point

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sincpt_c.html)
