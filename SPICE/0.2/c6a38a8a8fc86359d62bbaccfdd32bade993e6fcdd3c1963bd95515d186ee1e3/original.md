```
bodvrd(bodynm, item)
```

Fetch from the kernel pool the double precision values of an item associated with a body.

### Arguments

  * `bodynm`: Body name
  * `item`: Item for which values are desired. (`"RADII"`, `"NUT_PREC_ANGLES"`, etc.)
  * `maxn`: Maximum number of values that may be returned (default: 100)

### Output

  * `values`: Values

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/bodvrd_c.html)
