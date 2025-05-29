```
ekpsel(query, msglen=256, tablen=256, collen=256)
```

Parse the SELECT clause of an EK query, returning full particulars concerning each selected item.

### Arguments

  * `query`: EK query
  * `msglen`: Available space in the output error message string (default: 256)
  * `tablen`: Length of strings in `tabs` output array (default: 256)
  * `collen`: Length of strings in `cols` output array (default: 256)

### Output

  * `xbegs`: Begin positions of expressions in SELECT clause
  * `xends`: End positions of expressions in SELECT clause
  * `xtypes`: Data types of expressions
  * `xclass`: Classes of expressions
  * `tabs`: Names of tables qualifying SELECT columns
  * `cols`: Names of columns in SELECT clause of query

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ekpsel_c.html)
