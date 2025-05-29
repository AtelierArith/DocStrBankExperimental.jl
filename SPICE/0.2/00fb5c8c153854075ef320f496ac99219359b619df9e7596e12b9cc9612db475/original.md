```
unitim(epoch, insys, outsys)
```

Transform time from one uniform scale to another.

### Arguments

  * `epoch`: An epoch to be converted
  * `insys`: The time scale associated with the input epoch
  * `outsys`: The time scale associated with the function value

The uniform time scales are:

  * `:TAI`
  * `:TDT`
  * `:TDB`
  * `:ET`
  * `:JED`
  * `:JDTDB`
  * `:JDTDT`

### Output

Returns the time in the system specified by `outsys` that is equivalent to the `epoch` in the `insys` time scale.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/unitim_c.html)
