```
gfrfov(inst, raydir, rframe, abcorr, obsrvr, step, cnfine, maxwin=10000)
```

Determine time intervals when a specified ray intersects the space bounded by the field-of-view (FOV) of a specified instrument.

### Arguments

  * `inst`: Name of the instrument
  * `raydir`: Ray's direction vector
  * `rframe`: Reference frame of ray's direction vector
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `step`: Step size in seconds for finding FOV events
  * `cnfine`: SPICE window to which the search is restricted
  * `maxwin`: Maximum length of the output window (default: 10000)

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrfov_c.html)
