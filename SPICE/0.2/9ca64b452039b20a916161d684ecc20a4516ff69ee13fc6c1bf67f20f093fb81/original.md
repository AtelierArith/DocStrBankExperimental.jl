```
termpt(method, ilusrc, target, et, fixref, abcorr, corloc, obsrvr, refvec, rolstp,
       ncuts, schstp, soltol, maxn)
```

Find terminator points on a target body. The caller specifies half-planes, bounded by the illumination source center-target center vector, in which to search for terminator points.

The terminator can be either umbral or penumbral. The umbral terminator is the boundary of the region on the target surface where no light from the source is visible. The penumbral terminator is the boundary of the region on the target surface where none of the light from the source is blocked by the target itself.

The surface of the target body may be represented either by a triaxial ellipsoid or by topographic data.

### Arguments

  * `method`: Computation method
  * `ilusrc`: Illumination source
  * `target`: Name of target body
  * `et`: Epoch in ephemeris seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction
  * `corloc`: Aberration correction locus
  * `obsrvr`: Name of observing body
  * `refvec`: Reference vector for cutting half-planes
  * `rolstp`: Roll angular step for cutting half-planes
  * `ncuts`: Number of cutting planes
  * `schstp`: Angular step size for searching
  * `soltol`: Solution convergence tolerance
  * `maxn`: Maximum number of entries in output arrays

### Output

  * `npts`: Counts of terminator points corresponding to cuts
  * `points`: Terminator points
  * `epochs`: Times associated with terminator points
  * `trmvcs`: Terminator vectors emanating from the observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/termpt_c.html)
