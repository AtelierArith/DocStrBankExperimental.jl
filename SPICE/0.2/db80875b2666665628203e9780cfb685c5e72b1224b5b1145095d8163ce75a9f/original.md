```
gftfov(inst, target, tshape, tframe, abcorr, obsrvr, step, nintvls, cnfine)
```

Determine time intervals when a specified ephemeris object intersects the space bounded by the field-of-view (FOV) of a specified instrument.

### Arguments

  * `inst`: Name of the instrument
  * `target`: Name of the target body
  * `tshape`: Type of shape model used for target body
  * `tframe`: Body-fixed, body-centered frame for target body
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `step`: Step size in seconds for finding FOV events
  * `nintvls`: Workspace window interval count
  * `cnfine`: Window to which the search is restricted

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gftfov_c.html)
