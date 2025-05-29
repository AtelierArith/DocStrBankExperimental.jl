```
ekuced(handle, segno, recno, column, dvals, isnull)
```

Update a double precision column entry in a specified EK record.

### Arguments

  * `handle`: Handle attached to EK file
  * `segno`: Index of segment containing record
  * `recno`: Record in which entry is to be updated
  * `column`: Column name
  * `dvals`: Double precision values comprising new column entry
  * `isnull`: Flag indicating whether column entry is null

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekuced_c.html)
