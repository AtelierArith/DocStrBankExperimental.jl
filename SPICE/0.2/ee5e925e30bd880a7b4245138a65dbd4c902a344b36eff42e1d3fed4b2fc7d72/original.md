```
dlafns(handle, descr)
```

Find the segment following a specified segment in a DLA file.

### Arguments

  * `handle`: Handle of open DLA file
  * `descr`: Descriptor of a DLA segment

### Output

Returns the descriptor of the next segment in the DLA file or `nothing` if none was found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dlafns_c.html)
