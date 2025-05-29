```
ekgc(selidx, row, elment, lenout=256)
```

Return an element of an entry in a column of character type in a specified row.

### Arguments

  * `selidx`: Index of parent column in SELECT clause
  * `row`: Row to fetch from
  * `elment`: Index of element, within column entry, to fetch
  * `lenout`: Maximum length of column element (default: 256)

### Output

Returns the character string element of column entry or `missing` if it was null or `nothing` if the column was not found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekgc_c.html)
