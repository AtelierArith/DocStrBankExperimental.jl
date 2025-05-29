```
fits_open_image(filename::String, [mode = 0])
```

Open an existing data file (like [`fits_open_file`](@ref)) and move to the first HDU containing an image.

## Modes:

  * 0 : Read only (equivalently denoted by `CFITSIO.READONLY` or `CFITSIO.R`)
  * 1 : Read-write (equivalently denoted by `CFITSIO.READWRITE` or `CFITSIO.RW`)
