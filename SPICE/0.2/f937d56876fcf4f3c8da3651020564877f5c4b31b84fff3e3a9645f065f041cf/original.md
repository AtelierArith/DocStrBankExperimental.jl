```
fovray(inst, raydir, rframe, abcorr, observer, et)
```

Determine if a specified ray is within the field-of-view (FOV) of a specified instrument at a given time.

### Arguments

  * `inst`: Name or ID code string of the instrument
  * `raydir`: Ray's direction vector
  * `rframe`: Body-fixed, body-centered frame for target body
  * `abcorr`: Aberration correction flag
  * `observer`: Name or ID code string of the observer
  * `et`: Time of the observation (seconds past J2000)

### Output

Returns `true` if the ray is visible.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/fovray_c.html)
