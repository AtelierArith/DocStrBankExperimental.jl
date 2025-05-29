```
FortranFile(io::IO; kwargs...)
```

Wrap the given `IO` stream as a `FortranFile` containing Fortran "unformatted" (i.e. binary) data. The keyword arguments can be:

  * `access` for specifying the access mode; a `String` being one of

      * "sequential": sequential access as in Fortran, where records have leading and trailing record markers. This is the default.
      * "direct": direct access as in Fortran, where records have fixed length and can be accessed in random order. The "recl" keyword must be given to specify the record length. `read` and `write` operations on these files must use the `rec` keyword argument to specify which record to read/write.
  * `marker`: for specifying the type of record marker; one of

      * `RECMRK4B`: 4-byte record markers (with support for subrecords) [default]
      * `RECMRK8B`: 8-byte record markers

    This is ignored for direct access files.
  * `recl`: for specifying the record length if access=="direct". The record length is counted in bytes and must be specified as an Integer.
  * `convert`: for specifying the byte-order of the file data; one of

      * "native": use the host byte order [default]
      * "big-endian": use big-endian byte-order
      * "little-endian": use little-endian byte-order

The returned `FortranFile` can be used with Julia's `read` and `write` functions. See their documentation for more information.
