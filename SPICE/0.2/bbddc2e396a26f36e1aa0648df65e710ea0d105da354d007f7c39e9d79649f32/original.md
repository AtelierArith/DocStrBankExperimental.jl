```
ekgd(selidx, row, element)
```

Return an element of an entry in a column of double precision type in a specified row.

### Arguments

  * `selidx`: Index of parent column in SELECT clause
  * `row`: Row to fetch from
  * `elment`: Index of element, within column entry, to fetch

### Output

Returns the double precision element of column entry or `missing` if it was null or `nothing` if the column was not found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekgd_c.html)
