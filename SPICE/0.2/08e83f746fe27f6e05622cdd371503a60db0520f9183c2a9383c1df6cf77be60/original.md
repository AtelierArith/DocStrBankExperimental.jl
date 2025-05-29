```
lspcn(body, et, abcorr)
```

Compute L_s, the planetocentric longitude of the sun, as seen from a specified body.

### Arguments

  * `body`: Name of the central body
  * `et`: Epoch in seconds past J2000 TDB
  * `abcorr`: Aberration correction

### Output

Returns the planetocentric longitude of the sun for the specified body at the specified time in radians.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lspcn_c.html)
