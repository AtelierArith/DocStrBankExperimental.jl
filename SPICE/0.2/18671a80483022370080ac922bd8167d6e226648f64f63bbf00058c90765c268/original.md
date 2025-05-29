```
spkopn(name, ifname="", ncomch=0)
```

Create a new SPK file, returning the handle of the opened file.

### Arguments

  * `name`: The name of the new SPK file to be created
  * `ifname`: The internal filename for the SPK file (default: `""`)
  * `ncomch`: The number of characters to reserve for comments (default: 0)

### Output

Returns the handle of the opened SPK file.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkopn_c.html)
