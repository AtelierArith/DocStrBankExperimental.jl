```
spkcov!(cover, spk, idcode)
```

Find the coverage window for a specified ephemeris object in a specified SPK file.

### Arguments

  * `cover`: Window giving coverage in `spk` for `idcode`
  * `spk`: Name of the SPK file
  * `idcode`: ID code of ephemeris object

### Output

Returns the extended coverage window.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcov_c.html)
