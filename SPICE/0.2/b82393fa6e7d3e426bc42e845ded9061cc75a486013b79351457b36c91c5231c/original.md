```
getfat(file, arclen=10, typlen=10)
```

Determine the file architecture and file type of most SPICE kernel files.

### Arguments

  * `file`: The name of a file to be examined
  * `arclen`: Maximum length of output architecture string (default: 10)
  * `typlen`: Maximum length of output type string (default: 10)

### Output

  * `arch`: The architecture of the kernel file
  * `typ`: The type of the kernel file

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getfat_c.html)
