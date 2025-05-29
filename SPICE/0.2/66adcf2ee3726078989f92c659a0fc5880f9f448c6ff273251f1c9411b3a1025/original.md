```
dasrfr(handle, idwlen=128, ifnlen=256)
```

Read the contents of the file record of a DAS.

### Arguments

  * `handle`: DAS file handle
  * `idwlen`: Length of ID word string (default: 128)
  * `ifnlen`: Length of internal file name string (default: 256)

### Output

  * `idword`: ID word
  * `ifname`: DAS internal file name
  * `nresvr`: Number of reserved records in file
  * `nresvc`: Number of characters in use in reserved records area
  * `ncomr`: Number of comment records in file
  * `ncomc`: Number of characters in use in comment area

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dasrfr_c.html)
