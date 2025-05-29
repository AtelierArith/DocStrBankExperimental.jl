```
dafrfr(handle, lenout=128)
```

Read the contents of the file record of a DAF.

### Arguments

  * `handle`: Handle of an open DAF file
  * `lenout`: Available room in the output string `ifname` (default: 128)

### Output

  * `nd`: Number of double precision components in summaries
  * `ni`: Number of integer components in summaries
  * `ifname`: Internal file name
  * `fward`: Forward list pointer
  * `bward`: Backward list pointer
  * `free`: Free address pointer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dafrfr_c.html)
