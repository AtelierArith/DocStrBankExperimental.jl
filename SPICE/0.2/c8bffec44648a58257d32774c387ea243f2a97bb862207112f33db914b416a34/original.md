```
stpool(item, nth, contin, lenout=1024)
```

Retrieve the nth string from the kernel pool variable, where the string may be continued across several components of the kernel pool variable.

### Arguments

  * `item`: Name of the kernel pool variable
  * `nth`: Index of the full string to retrieve
  * `contin`: Character sequence used to indicate continuation
  * `lenout`: Available space in output string (default: 1024)

### Output

Returns the full string concatenated across continuations if the kernel variable was found or `nothing` otherwise.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/stpool_c.html)
