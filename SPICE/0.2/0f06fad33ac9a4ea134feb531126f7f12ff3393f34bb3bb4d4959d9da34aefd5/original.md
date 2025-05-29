```
phaseq(et, target, illmn, obsrvr, abcorr)
```

Compute the apparent phase angle for a target, observer, illuminator set of ephemeris objects.

### Arguments

  * `et`: Ephemeris seconds past J2000 TDB
  * `target`: Target body name
  * `illmn`: Illuminating body name
  * `obsrvr`: Observer body
  * `abcorr`: Aberration correction flag

### Output

Returns the value of the phase angle.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/phaseq_c.html)
