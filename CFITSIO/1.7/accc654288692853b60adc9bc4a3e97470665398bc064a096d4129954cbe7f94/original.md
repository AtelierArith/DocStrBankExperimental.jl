```
fits_open_file(filename::String, [mode = 0])
```

Open an existing data file.

## Modes:

  * 0 : Read only (equivalently denoted by `CFITSIO.READONLY` or `CFITSIO.R`)
  * 1 : Read-write (equivalently denoted by `CFITSIO.READWRITE` or `CFITSIO.RW`)

This function uses the extended filename syntax to open the file. See also [`fits_open_diskfile`](@ref) that does not use the extended filename parser and uses `filename` as is as the name of the file.
