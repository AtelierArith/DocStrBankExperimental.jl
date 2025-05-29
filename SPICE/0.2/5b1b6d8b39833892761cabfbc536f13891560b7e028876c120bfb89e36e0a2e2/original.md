```
kinfo(file, srclen=256)
```

### Arguments

  * `file`: Name of a kernel to fetch information for
  * `srclen`: Available space in output source string

### Output

Returns `nothing` if no kernel was found or a tuple consisting of

  * `filtyp`: The type of the kernel
  * `source`: Name of the source file used to load file
  * `handle`: The handle attached to file

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kinfo_c.html)
