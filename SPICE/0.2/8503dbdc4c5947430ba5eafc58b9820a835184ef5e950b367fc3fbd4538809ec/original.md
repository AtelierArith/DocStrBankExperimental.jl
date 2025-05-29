```
bodvcd(bodyid, item)
```

Fetch from the kernel pool the double precision values of an item associated with a body, where the body is specified by an integer ID code.

### Arguments

  * `bodyid`: Body ID code
  * `item`: Item for which values are desired. (`"RADII"`, `"NUT_PREC_ANGLES"`, etc.)
  * `maxn`: Maximum number of values that may be returned (default: 100)

### Output

Returns the requested values.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/bodvcd_c.html)
