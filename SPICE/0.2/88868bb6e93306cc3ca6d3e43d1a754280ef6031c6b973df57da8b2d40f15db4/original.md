```
sce2t(sc, et)
```

Convert ephemeris seconds past J2000 (ET) to integral encoded spacecraft clock ("ticks"). For conversion to fractional ticks, (required for C-kernel production), see the routine [`sce2c`](@ref).

### Arguments

  * `sc`: NAIF spacecraft ID code
  * `et`: Ephemeris time, seconds past J2000

### Output

Returns SCLK, encoded as ticks since spacecraft clock start.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sce2c_t.html)
