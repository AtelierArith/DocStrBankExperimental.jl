```
fits_open_data(filename::String, [mode = 0])
```

Open an existing data file (like [`fits_open_file`](@ref)) and move to the first HDU containing either an image or a table.

## Modes:

  * 0 : Read only (equivalently denoted by `CFITSIO.R`)
  * 1 : Read-write (equivalently denoted by `CFITSIO.RW`)
