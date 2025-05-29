```
sce2s(sc, et, lenout=128)
```

Convert an epoch specified as ephemeris seconds past J2000 (ET) to a character string representation of a spacecraft clock value (SCLK).

### Arguments

  * `sc`: NAIF spacecraft identification code
  * `et`: Ephemeris time, specified as seconds past J2000
  * `lenout`: Maximum allowed length of output SCLK string

### Output

Returns an SCLK string.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2s_c.html)
