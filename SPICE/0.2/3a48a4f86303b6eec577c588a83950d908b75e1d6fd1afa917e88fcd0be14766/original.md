```
scdecd(sc, sclkdp, lenout=128)
```

Convert double precision encoding of spacecraft clock time into a character representation.

### Arguments

  * `sc`: NAIF spacecraft identification code
  * `sclkdp`: Encoded representation of a spacecraft clock count
  * `lenout`: Maximum allowed length of output SCLK string

### Output

Returns the character representation of a clock count.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/scdecd_c.html)
