```
fovtrg(inst, target, tshape, tframe, abcorr, obsrvr, et)
```

Determine if a specified ephemeris object is within the field-of-view (FOV) of a specified instrument at a given time.

### Arguments

  * `inst`: Name or ID code string of the instrument.
  * `target`: Name or ID code string of the target.
  * `tshape`: Type of shape model used for the target.
  * `tframe`: Body-fixed, body-centered frame for target body.
  * `abcorr`: Aberration correction flag.
  * `obsrvr`: Name or ID code string of the observer.
  * `et`: Time of the observation (seconds past J2000).

### Output

Returns `true` if the object is visible.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/fovtrg_c.html)
