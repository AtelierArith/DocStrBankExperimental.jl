```
timout(et, pictur, lenout=128)
```

This routine converts an input epoch represented in TDB seconds past the TDB epoch of J2000 to a character string formatted to the specifications of a user's format picture.

### Arguments

  * `et`: An epoch in seconds past the ephemeris epoch J2000
  * `pictur`: A format specification for the output string
  * `lenout`: The length of the output string plus 1 (default: 128)

### Output

Returns a string representation of the input epoch.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/timout_c.html)
