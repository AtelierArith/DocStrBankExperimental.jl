```
dskd02(handle, dladsc, item, start, room)
```

Fetch double precision data from a type 2 DSK segment.

### Arguments

  * `handle`: DSK file handle
  * `dladsc`: DLA descriptor
  * `item`: Keyword identifying item to fetch
  * `start`: Start index
  * `room`: Amount of room in output array

### Output

Returns an array containing the requested item.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskd02_c.html)
