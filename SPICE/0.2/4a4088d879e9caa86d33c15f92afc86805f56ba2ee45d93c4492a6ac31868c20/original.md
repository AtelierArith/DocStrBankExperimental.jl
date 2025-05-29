```
spksfs(body, et)
```

Search through loaded SPK files to find the highest-priority segment applicable to the body and time specified.

### Arguments

  * `body`: Body ID
  * `et`: Ephemeris time

### Output

Returns `nothing` if no segment was found or a tuple consisting of:

  * `handle`: Handle of file containing the applicable segment
  * `descr`: Descriptor of the applicable segment
  * `ident`: Identifier of the applicable segment

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spksfs_c.html)
