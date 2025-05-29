```
srfnrm(method, target, et, fixref, npts, srfpts)
```

Map array of surface points on a specified target body to the corresponding unit length outward surface normal vectors.

The surface of the target body may be represented by a triaxial ellipsoid or by topographic data provided by DSK files.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `et`: Epoch in TDB seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `srfpts`: Array of surface points

### Output

Returns an array of outward, unit length normal vectors.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfnrm_c.html)
