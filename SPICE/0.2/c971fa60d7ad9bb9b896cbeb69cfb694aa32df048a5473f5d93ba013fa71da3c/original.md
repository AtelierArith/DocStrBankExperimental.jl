```
dafgsr(handle, recno, start, stop)
```

Read a portion of the contents of a summary record in a DAF file.

### Arguments

  * `handle`: Handle of DAF
  * `recno`: Record number
  * `start`: First word to read from record
  * `stop`: Last word to read from record

### Output

Returns the contents of the record or `nothing` if none was found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dafgsr_c.html)
