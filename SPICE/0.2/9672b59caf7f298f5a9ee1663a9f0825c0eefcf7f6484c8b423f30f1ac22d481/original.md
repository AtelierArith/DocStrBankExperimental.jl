```
gnpool(name, start, room, lenout=128)
```

Return names of kernel variables matching a specified template.

### Arguments

  * `name`: Template that names should match
  * `start`: Index of first matching name to retrieve
  * `room`: The largest number of values to return
  * `lenout`: Length of strings in output array `kvars` (default: 128)

### Output

Returns lernel pool variables whose names match `name`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gnpool_c.html)
