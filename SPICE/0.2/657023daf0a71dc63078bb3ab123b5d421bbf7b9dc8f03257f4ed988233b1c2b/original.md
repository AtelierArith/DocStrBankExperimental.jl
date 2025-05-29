```
srfcss(code, bodstr)
```

Translate a surface ID code, together with a body string, to the corresponding surface name. If no such surface name exists, return a string representation of the surface ID code.

### Arguments

  * `code`: Integer surface ID code to translate to a string
  * `bodstr`: Name or ID of body associated with surface

### Output

  * `srfstr`: String corresponding to surface ID code
  * `isname`: Logical flag indicating output is a surface name

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfcss_c.html)
