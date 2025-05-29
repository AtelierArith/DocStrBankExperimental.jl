```
limbpt(method, target, et, fixref, abcorr, corloc, obsrvr, refvec, rolstp, ncuts, schstp,
       soltol, maxn)
```

Find limb points on a target body. The limb is the set of points of tangency on the target of rays emanating from the observer.  The caller specifies half-planes bounded by the observer-target center vector in which to search for limb points.

The surface of the target body may be represented either by a triaxial ellipsoid or by topographic data.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in ephemeris seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction
  * `corloc`: Aberration correction locus
  * `obsrvr`: Name of observing body
  * `refvec`: Reference vector for cutting half-planes
  * `rolstp`: Roll angular step for cutting half-planes
  * `ncuts`: Number of cutting half-planes
  * `schstp`: Angular step size for searching
  * `soltol`: Solution convergence tolerance
  * `maxn`: Maximum number of entries in output arrays

### Output

Returns the tuple `(npts, points, epochs, tangts)`.

  * `npts`: Counts of limb points corresponding to cuts
  * `points`: Limb points
  * `epochs`: Times associated with limb points
  * `tangts`: Tangent vectors emanating from the observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lgrind_c.html)
