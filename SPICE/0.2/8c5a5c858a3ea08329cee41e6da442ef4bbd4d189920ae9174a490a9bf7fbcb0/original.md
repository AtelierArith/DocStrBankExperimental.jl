```
wnsumd(window)
```

Summarize the contents of a double precision window.

### Arguments

  * `window`: Window to be summarized

### Output

Returns a tuple consisting of:

  * `meas`: Total measure of intervals in window
  * `avg`: Average measure
  * `stddev`: Standard deviation
  * `shortest`: Location of shortest interval
  * `longest`: Location of longest interval

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/wnsumd_c.html)
