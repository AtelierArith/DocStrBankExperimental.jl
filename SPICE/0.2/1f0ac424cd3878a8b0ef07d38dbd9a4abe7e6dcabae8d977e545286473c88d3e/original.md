```
frinfo(frcode)
```

Retrieve the minimal attributes associated with a frame needed for converting transformations to and from it.

### Arguments

  * `frcode`: The id code for a reference frame

### Output

  * `cent`: The center of the frame
  * `frclss`: The class (type) of the frame
  * `clssid`: The idcode for the frame within its class

Returns `nothing` if no frame with id `frcode` could be found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/frinfo_c.html)
