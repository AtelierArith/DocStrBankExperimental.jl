```
latsrf(method, target, et, fixref, npts, lonlat)
```

Map array of planetocentric longitude/latitude coordinate pairs to surface points on a specified target body.

The surface of the target body may be represented by a triaxial ellipsoid or by topographic data provided by DSK files.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in TDB seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `lonlat`: Array of longitude/latitude coordinate pairs

### Output

Returns an array of surface points.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/latsrf_c.html)
