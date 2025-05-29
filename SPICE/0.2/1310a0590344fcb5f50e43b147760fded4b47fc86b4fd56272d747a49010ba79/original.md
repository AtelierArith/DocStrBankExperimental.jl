```
gfilum(method, angtyp, target, illmn, fixref, abcorr, obsrvr, spoint, relate, refval,
       adjust, step, nintvls, cnfine)
```

Return the time window over which a specified constraint on the observed phase, solar incidence, or emission angle at a specifed target body surface point is met.

### Arguments

  * `method`: Computation method
  * `angtyp`: Type of illumination angle
  * `target`: Name of the target body
  * `illmn`: Name of the illumination source
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `spoint`: Body-fixed coordinates of a target surface point
  * `relate`: Relational operator
  * `refval`: Reference value
  * `adjust`: Adjustment value for absolute extrema searches
  * `step`: Step size used for locating extrema and roots
  * `nintvls`: Workspace window interval count
  * `cnfine`: Window to which the search is confined

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfilum_c.html)
