```
gfocce!(occtyp, front, fshape, fframe, back, bshape, bframe, abcorr, obsrvr, tol,
        udstep, udrefn, rpt, udrepi, udrepu, udrepf, cnfine, result)
```

Determine time intervals when an observer sees one target occulted by another.

### Arguments

  * `occtyp`: Type of occultation
  * `front`: Name of body occulting the other
  * `fshape`: Type of shape model used for front body
  * `fframe`: Body-fixed, body-centered frame for front body
  * `back`: Name of body occulted by the other
  * `bshape`: Type of shape model used for back body
  * `bframe`: Body-fixed, body-centered frame for back body
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `tol`: Convergence tolerance in seconds
  * `udstep`: Name of the routine that returns a time step
  * `udrefn`: Name of the routine that computes a refined time
  * `rpt`: Progress report flag
  * `udrepi`: Function that initializes progress reporting
  * `udrepu`: Function that updates the progress report
  * `udrepf`: Function that finalizes progress reporting
  * `cnfine`: SPICE window to which the search is restricted
  * `result`: SPICE window containing results

### Output

Returns `result`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfocce_c.html)
