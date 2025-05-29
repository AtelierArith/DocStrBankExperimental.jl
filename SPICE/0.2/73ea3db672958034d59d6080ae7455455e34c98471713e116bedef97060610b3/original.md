```
gfudb!(udfuns, udfunb, step, cnfine, result)
```

Perform a GF search on a user defined boolean quantity.

### Arguments

  * `udfuns`: Name of the routine that computes a scalar quantity of interest corresponding to an `et`, e.g. `f(et) = ...`
  * `udfunb`: Name of the routine returning the boolean value corresponding to an `et`, e.g. `g(f, et) = ...`
  * `step`: Step size used for locating extrema and roots
  * `cnfine`: Window to which the search is restricted
  * `result`: Window containing results

### Output

Returns `result`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfudb_c.html)
