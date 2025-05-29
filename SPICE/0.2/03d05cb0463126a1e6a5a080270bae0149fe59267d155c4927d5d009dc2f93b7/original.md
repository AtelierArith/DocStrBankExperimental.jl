```
gcpool(name; start=1, room=100, lenout=128)
```

Return the value of a kernel variable from the kernel pool.

### Arguments

  * `name`: Name of the variable whose value is to be returned
  * `start`: Which component to start retrieving for name (default: 1)
  * `room`: The largest number of values to return (default: 100)
  * `lenout`: The length of the longest string to return (default: 128)

### Output

Returns an array of values if the variable exists or `nothing` if not.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gcpool_c.html)
