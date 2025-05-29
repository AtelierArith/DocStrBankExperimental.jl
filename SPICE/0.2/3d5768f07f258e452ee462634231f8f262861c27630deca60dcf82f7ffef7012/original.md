```
ekrced(handle, segno, recno, column, nelts=100)
```

Read data from a double precision column in a specified EK record.

### Arguments

  * `handle`: Handle attached to EK file
  * `segno`: Index of segment containing record
  * `recno`: Record from which data is to be read
  * `column`: Column name
  * `nelts`: Maximum number of elements to return (default: 100)

### Output

Returns the values in column entry.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekrced_c.html)
