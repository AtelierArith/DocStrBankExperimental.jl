```
ekacld(handle, segno, column, dvals, nlflgs, rcptrs)
```

Add an entire double precision column to an EK segment.

### Arguments

  * `handle`: EK file handle
  * `segno`: Number of segment to add column to
  * `column`: Column name
  * `dvals`: Double precision values to add to column
  * `nlflgs`: Array of null flags for column entries
  * `rcptrs`: Record pointers for segment

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekacld_c.html)
