```
gfsntc(target, fixref, method, abcorr, obsrvr, dref, dvec, crdsys, coord, relate, refval,
       adjust, step, nintvls, cnfine)
```

Determine time intervals for which a coordinate of an surface intercept position vector satisfies a numerical constraint.

### Arguments

  * `target`: Name of the target body
  * `fixref`: Body fixed frame associated with `target`
  * `method`: Name of method type for surface intercept calculation
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `dref`: Reference frame of direction vector `dvec`
  * `dvec`: Pointing direction vector from `obsrvr`
  * `crdsys`: Name of the coordinate system containing COORD
  * `coord`: Name of the coordinate of interest
  * `relate`: Operator that either looks for an extreme value (max, min, local, absolute) or compares the coordinate value and `refval`
  * `refval`: Reference value
  * `adjust`: Adjustment value for absolute extrema searches
  * `step`: Step size used for locating extrema and roots
  * `nintvls`: Workspace window interval count
  * `cnfine`: Window to which the search is restricted

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfsntc_c.html)
