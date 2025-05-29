```
ekacli(handle, segno, column, ivals, nlflgs, rcptrs)
```

Add an entire integer column to an EK segment.

### Arguments

  * `handle`: EK file handle
  * `segno`: Number of segment to add column to
  * `column`: Column name
  * `ivals`: Integer values to add to column
  * `nlflgs`: Array of null flags for column entries
  * `rcptrs`: Record pointers for segment

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekacli_c.html)
