```
pckcov!(cover, pck, idcode)
```

Find the coverage window for a specified reference frame in a specified binary PCK file.

### Arguments

  * `cover`: An initalized window `SpiceDoubleCell`
  * `pck`: Path of PCK file
  * `idcode`: Class ID code of PCK reference frame

### Output

Returns `cover` containing coverage in `pck` for `idcode`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/pckcov_c.html)
