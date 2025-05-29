```
sct2e(sc, sclkdp)
```

Convert encoded spacecraft clock ("ticks") to ephemeris seconds past J2000 (ET).

### Arguments

  * `sc`: NAIF integer code for a spacecraft
  * `sclkdp`: SCLK, encoded as ticks since spacecraft clock start.

### Output

Returns ephemeris time seconds past J2000.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sct2e_c.html)
