```
ekifld(handle, tabnam, nrows, cnames, decls)
```

Initialize a new E-kernel segment to allow fast writing.

### Arguments

  * `handle`: File handle
  * `tabnam`: Table name
  * `nrows`: Number of rows in the segment
  * `cnames`: Names of columns
  * `decls`: Declarations of columns

### Output

  * `segno`: Segment number
  * `rcptrs`: Array of record pointers

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekifld_c.html)
