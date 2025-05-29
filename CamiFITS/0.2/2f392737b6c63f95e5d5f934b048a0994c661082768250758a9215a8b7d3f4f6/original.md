```
FITS_dataobject
```

Object to hold the data of the [`FITS_HDU`](@ref) of given `hdutype`.

The fields are:

  * `.hdutype`:  accepted types are 'PRIMARY', 'IMAGE' and 'TABLE' (`::String`)
  * `.data`:  in the from appropriate for the `hdutype` (::Any)
