```
dskxsi(pri, target, nsurf, srflst, et, fixref, vertex, raydir, maxd=1, maxi=1)
```

Compute a ray-surface intercept using data provided by multiple loaded DSK segments. Return information about the source of the data defining the surface on which the intercept was found: DSK handle, DLA and DSK descriptors, and DSK data type-dependent parameters.

### Arguments

  * `pri`: Data prioritization flag
  * `target`: Target body name
  * `srflst`: Surface ID list
  * `et`: Epoch, expressed as seconds past J2000 TDB
  * `fixref`: Name of target body-fixed reference frame
  * `vertex`: Vertex of ray
  * `raydir`: Direction vector of ray
  * `maxd`: Size of DC array (default: 1)
  * `maxi`: Size of IC array (default: 1)

### Output

Returns `nothing` if no intercept exists or

  * `xpt`: Intercept point
  * `handle`: Handle of segment contributing surface data
  * `dladsc`: DLA descriptor of segment
  * `dskdsc`: DSK descriptor of segment
  * `dc`: Double precision component of source info
  * `ic`: Integer component of source info

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskxsi_c.html)
