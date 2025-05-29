```
occult(targ1, shape1, frame1, targ2, shape2, frame2, abcorr, obsrvr, et)
```

Determines the occultation condition (not occulted, partially, etc.) of one target relative to another target as seen by an observer at a given time.

The surfaces of the target bodies may be represented by triaxial ellipsoids or by topographic data provided by DSK files.

### Arguments

  * `targ1`: Name or ID of first target.
  * `shape1`: Type of shape model used for first target.
  * `frame1`: Body-fixed, body-centered frame for first body.
  * `targ2`: Name or ID of second target.
  * `shape2`: Type of shape model used for second target.
  * `frame2`: Body-fixed, body-centered frame for second body.
  * `abcorr`: Aberration correction flag.
  * `obsrvr`: Name or ID of the observer.
  * `et`: Time of the observation (seconds past J2000).

### Output

Returns the occultation identification code.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/occult_c.html)
