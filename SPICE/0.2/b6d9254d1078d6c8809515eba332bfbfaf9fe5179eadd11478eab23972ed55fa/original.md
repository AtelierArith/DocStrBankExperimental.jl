```
bodfnd(body, item)
```

Determine whether values exist for some item for any body in the kernel pool.

### Arguments

  * `body`: ID code of body
  * `item`: Item to find (`"RADII"`, `"NUT_AMP_RA"`, etc.)

### Output

Returns `true` if the item is in the kernel pool and `false` if it is not.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/bodfnd_c.html)
