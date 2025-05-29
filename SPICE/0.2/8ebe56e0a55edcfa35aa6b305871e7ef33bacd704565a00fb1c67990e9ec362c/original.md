```
sce2c(sc, et)
```

Convert ephemeris seconds past J2000 (ET) to continuous encoded spacecraft clock ("ticks"). Non-integral tick values may be returned.

### Arguments

  * `sc`: NAIF spacecraft ID code
  * `et`: Ephemeris time, seconds past J2000

### Output

Returns SCLK, encoded as ticks since spacecraft clock start.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2c_c.html)
