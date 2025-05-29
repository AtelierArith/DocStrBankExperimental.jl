```
ekaced(handle, segno, recno, column, dvals, isnull)
```

Add data to an double precision column in a specified EK record.

### Arguments

  * `handle`: EK file handle
  * `segno`: Index of segment containing record
  * `recno`: Record to which data is to be added
  * `column`: Column name
  * `dvals`: Double precision values to add to column
  * `isnull`: Flag indicating whether column entry is null

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekaced_c.html)
