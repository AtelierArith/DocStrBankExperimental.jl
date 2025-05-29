```
ckcov!(ck, idcode, needav, level, tol, timsys, cover)
```

Find the coverage window for a specified object in a specified CK file.

### Arguments

  * `ck`: Name of CK file
  * `idcode`: ID code of object
  * `needav`: Flag indicating whether angular velocity is needed
  * `level`: Coverage level:  "SEGMENT" OR "INTERVAL"
  * `tol`: Tolerance in ticks
  * `timsys`: Time system used to represent coverage
  * `cover`: Window giving coverage for `idcode`. Data already present in `cover`   will be combined with coverage found for the object designated by `idcode`   in the file `ck`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ckcov_c.html)
