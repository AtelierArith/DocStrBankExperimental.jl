```
ekrcec(handle, segno, recno, column, lenout=256, nelts=100)
```

Read data from a character column in a specified EK record.

### Arguments

  * `handle`: Handle attached to EK file
  * `segno`: Index of segment containing record
  * `recno`: Record from which data is to be read
  * `column`: Column name
  * `lenout`: Maximum length of output strings
  * `nelts`: Maximum number of elements to return (default: 100)

### Output

Returns the character values in column entry or `missing` if they are null.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekrcec_c.html)
