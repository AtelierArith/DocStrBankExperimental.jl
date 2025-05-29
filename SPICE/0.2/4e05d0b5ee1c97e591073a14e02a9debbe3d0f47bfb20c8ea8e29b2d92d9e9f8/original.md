```
etcal(et, lenout=128)
```

Convert from an ephemeris epoch measured in seconds past the epoch of J2000 to a calendar string format using a formal calendar free of leapseconds.

### Arguments

  * `et`: Ephemeris time measured in seconds past J2000
  * `lenout`: Length of output string (default: 128)

### Output

Returns a standard calendar representation of `et`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/etcal_c.html)
