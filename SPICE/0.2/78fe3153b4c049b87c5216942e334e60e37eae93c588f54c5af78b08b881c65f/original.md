```
ekaclc(handle, segno, column, cvals, nlflgs, rcptrs)
```

Add an entire character column to an EK segment.

### Arguments

  * `handle`: EK file handle.
  * `segno`: Number of segment to add column to.
  * `column`: Column name.
  * `cvals`: Character values to add to column.
  * `nlflgs`: Array of null flags for column entries.
  * `rcptrs`: Record pointers for segment.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekaclc_c.html)
