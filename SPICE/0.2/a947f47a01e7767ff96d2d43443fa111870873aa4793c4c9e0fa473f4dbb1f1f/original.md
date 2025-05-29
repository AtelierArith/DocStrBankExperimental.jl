```
ekcii(table, cindex, lenout=256)
```

Return attribute information about a column belonging to a loaded EK table, specifying the column by table and index.

### Arguments

  * `table`: Name of table containing column
  * `cindex`: Index of column whose attributes are to be found
  * `lenout`: Maximum allowed length of column name (default: 256)

### Output

  * `column`: Name of column
  * `attdsc`: Column attribute descriptor

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekcii_c.html)
