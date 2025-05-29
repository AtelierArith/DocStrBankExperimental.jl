```
edterm(trmtyp, source, target, et, fixref, abcorr, obsrvr, npts)
```

Compute a set of points on the umbral or penumbral terminator of a specified target body, where the target shape is modeled as an ellipsoid.

### Arguments

  * `trmtyp`: Terminator type
  * `source`: Light source
  * `target`: Target body
  * `et`: Observation epoch
  * `fixref`: Body-fixed frame associated with target
  * `abcorr`: Aberration correction
  * `obsrvr`: Observer
  * `npts`: Number of points in terminator set

### Output

  * `trgepc`: Epoch associated with target center
  * `obspos`: Position of observer in body-fixed frame
  * `trmpts`: Terminator point set

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/edterm_c.html)
