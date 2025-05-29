```
getelm(frstyr, lines)
```

Given the "lines" of a two-line element set, parse the lines and return the elements in units suitable for use in SPICE software.

### Arguments

  * `frstyr`: Year of earliest representable two-line elements
  * `lines`: A pair of "lines" containing two-line elements

### Output

  * `epoch`: The epoch of the elements in seconds past J2000
  * `elems`: The elements converted to SPICE units

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getelm_c.html)
