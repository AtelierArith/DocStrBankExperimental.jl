```
ekucec(handle, segno, recno, column, cvals, isnull)
```

Update a character column entry in a specified EK record.

### Arguments

  * `handle`: EK file handle
  * `segno`: Index of segment containing record
  * `recno`: Record to which data is to be updated
  * `column`: Column name
  * `cvals`: Character values comprising new column entry
  * `isnull`: Flag indicating whether column entry is null

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekucec_c.html)
