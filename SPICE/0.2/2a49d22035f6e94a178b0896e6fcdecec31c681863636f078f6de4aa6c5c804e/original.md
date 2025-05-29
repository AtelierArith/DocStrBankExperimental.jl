```
dskxv(pri, target, srflst, et, fixref, nrays, vtxarr, dirarr)
```

Compute ray-surface intercepts for a set of rays, using data provided by multiple loaded DSK segments.

### Arguments

  * `pri`: Data prioritization flag
  * `target`: Target body name
  * `srflst`: Surface ID list
  * `et`: Epoch, expressed as seconds past J2000 TDB
  * `fixref`: Name of target body-fixed reference frame
  * `nrays`: Number of rays
  * `vtxarr`: Array of vertices of rays
  * `dirarr`: Array of direction vectors of rays

### Output

  * `xptarr`: Intercept point array
  * `fndarr`: Found flag array

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskxv_c.html)
