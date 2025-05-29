```
dskobj!(set, dsk)
```

Find the set of body ID codes of all objects for which topographic data are provided in a specified DSK file.

### Arguments

  * `dsk`: Name of DSK file
  * `set` or `len`: Either a preallocated `SpiceIntCell` or the `size` of the output set.

### Output

Returns the set of ID codes of objects in the DSK file.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskobj_c.html)
