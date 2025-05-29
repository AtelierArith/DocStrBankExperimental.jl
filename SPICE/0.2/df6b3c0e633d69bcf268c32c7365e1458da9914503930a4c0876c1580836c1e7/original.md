```
cidfrm(cent)
```

Retrieve frame ID code and name to associate with a frame center.

### Arguments

  * `cent`: ID code for an object for which there is a preferred reference frame

### Output

Returns `nothing` if no frame was found or

  * `frcode`: The ID code of the frame associated with `cent`
  * `frname`: The name of the frame with ID `frcode`

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/cidfrm_c.html)
