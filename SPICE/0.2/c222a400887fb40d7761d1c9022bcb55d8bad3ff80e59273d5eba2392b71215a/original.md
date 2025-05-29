```
gfrr(target, abcorr, obsrvr, relate, refval, adjust, step, nintvls, cnfine)
```

Determine time intervals for which a specified constraint on the observer-target range rate is met.

### Arguments

  * `target`: Name of the target body
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `relate`: Relational operator
  * `refval`: Reference value
  * `adjust`: Adjustment value for absolute extrema searches
  * `step`: Step size used for locating extrema and roots
  * `nintvls`: Workspace window interval count
  * `cnfine`: Window to which the search is confined

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrr_c.html)
