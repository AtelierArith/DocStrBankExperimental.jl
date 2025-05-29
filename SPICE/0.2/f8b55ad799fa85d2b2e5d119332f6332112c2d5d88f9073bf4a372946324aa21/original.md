```
gffove!(inst, tshape, raydir, target, tframe, abcorr, obsrvr, tol,
        udstep, udrefn, rpt, udrepi, udrepu, udrepf, cnfine, result)
```

Determine time intervals when a specified target body or ray intersects the space bounded by the field-of-view (FOV) of a specified instrument.

### Arguments

  * `inst`: Name of the instrument
  * `tshape`: Type of shape model used for target body
  * `raydir`: Ray's direction vector
  * `target`: Name of the target body
  * `tframe`: Body-fixed, body-centered frame for target body
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `tol`: Convergence tolerance in seconds
  * `udstep`: Name of the routine returns a time step
  * `udrefn`: Name of the routine that computes a refined time
  * `rpt`: Progress report flag
  * `udrepi`: Function that initializes progress reporting
  * `udrepu`: Function that updates the progress report
  * `udrepf`: Function that finalizes progress reporting
  * `cnfine`: SPICE window to which the search is restricted
  * `result`: Window containing the results

### Output

Returns `result`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gffove_c.html)
