```
srfc2s(code, bodyid)
```

Translate a surface ID code, together with a body ID code, to the corresponding surface name. If no such name exists, return a string representation of the surface ID code.

### Arguments

  * `code`: Integer surface ID code to translate to a string
  * `bodyid`: ID code of body associated with surface

### Output

  * `srfstr`: String corresponding to surface ID code
  * `isname`: Logical flag indicating output is a surface name

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/srfc2s_c.html)
