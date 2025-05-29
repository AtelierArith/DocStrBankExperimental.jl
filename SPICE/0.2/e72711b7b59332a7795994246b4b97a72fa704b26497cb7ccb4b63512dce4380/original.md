```
gfoclt(occtyp, front, fshape, fframe, back, bshape, bframe, abcorr, obsrvr, step, cnfine,
       maxwin=100)
```

Determine time intervals when an observer sees one target occulted by, or in transit across, another.

The surfaces of the target bodies may be represented by triaxial ellipsoids or by topographic data provided by DSK files.

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
  * `step`: Step size in seconds for finding occultation events
  * `cnfine`: Window to which the search is restricted
  * `maxwin`: Maximum size of the output window (default: 100)

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfoclt_c.html)
