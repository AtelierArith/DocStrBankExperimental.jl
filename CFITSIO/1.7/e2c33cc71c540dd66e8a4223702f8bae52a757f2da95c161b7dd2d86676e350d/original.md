```
fits_open_diskfile(filename::String, [mode = 0])
```

Open an existing data file.

## Modes:

  * 0 : Read only (equivalently denoted by `CFITSIO.READONLY` or `CFITSIO.R`)
  * 1 : Read-write (equivalently denoted by `CFITSIO.READWRITE` or `CFITSIO.RW`)

This function does not use the extended filename parser, and uses `filename` as is as the name of the file that is to be opened. See also [`fits_open_file`](@ref) which uses the extended filename syntax.
