```
ckopn(fname, ifname="CK_file", ncomch=0)
```

Open a new CK file, returning the handle of the opened file.

### Arguments

  * `fname`: The name of the CK file to be opened
  * `ifname`: The internal filename for the CK (default: "`CK_file`")
  * `ncomch`: The number of characters to reserve for comments (default: 0)

### Output

  * `handle`: The handle of the opened CK file

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckopn_c.html)
