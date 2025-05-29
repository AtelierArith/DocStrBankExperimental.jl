```
kdata(which, kind, fillen=1024, srclen=256)
```

Return data for the n-th kernel that is among a list of specified kernel types.

### Arguments

  * `which`: Index of kernel to fetch from the list of kernels
  * `kind`: The kind of kernel to which fetches are limited
  * `fillen`: Available space in output file string
  * `srclen`: Available space in output source string

### Output

Returns `nothing` if no kernel was found or a tuple consisting of

  * `file`: The name of the kernel file
  * `filtyp`: The type of the kernel
  * `source`: Name of the source file used to load file
  * `handle`: The handle attached to file

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kdata_c.html)
