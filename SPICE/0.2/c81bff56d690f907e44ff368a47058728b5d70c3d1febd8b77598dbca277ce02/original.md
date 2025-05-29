```
ekacec(handle, segno, recno, column, cvals, isnull)
```

Add data to a character column in a specified EK record.

### Arguments

  * `handle`: EK file handle
  * `segno`: Index of segment containing record
  * `recno`: Record to which data is to be added
  * `column`: Column name
  * `cvals`: Character values to add to column
  * `isnull`: Flag indicating whether column entry is null

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekacec_c.html)
