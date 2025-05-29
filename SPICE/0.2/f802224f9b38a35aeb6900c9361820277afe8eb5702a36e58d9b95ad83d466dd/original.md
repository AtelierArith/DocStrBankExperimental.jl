```
gfuds!(udfuns, udqdec, relate, refval, adjust, step, nintvls, cnfine, result)
```

Perform a GF search on a user defined scalar quantity.

### Arguments

  * `udfuns`: Name of the routine that computes the scalar quantity of interest at some time, e.g. `f(et) = ...`
  * `udqdec`: Name of the routine that computes whether the scalar quantity is decreasing, e.g. `g(f, et) = ...`
  * `relate`: Operator that either looks for an extreme value (max, min, local, absolute) or compares the geometric quantity value and a number
  * `refval`: Value used as reference for scalar quantity condition
  * `adjust`: Allowed variation for absolute extremal geometric conditions
  * `step`: Step size used for locating extrema and roots
  * `nintvls`: Workspace window interval count
  * `cnfine`: SPICE window to which the search is restricted
  * `result`: SPICE window containing results

### Output

Returns `result`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfuds_c.html)
