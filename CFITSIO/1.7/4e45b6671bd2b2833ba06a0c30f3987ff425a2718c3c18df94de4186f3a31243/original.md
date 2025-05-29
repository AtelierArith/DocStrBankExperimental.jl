```
fits_create_file(filename::AbstractString)
```

Create and open a new empty output `FITSFile`. This methods uses the [extended file name syntax](https://heasarc.gsfc.nasa.gov/docs/software/fitsio/c/c_user/node83.html) to create the file.

See also [`fits_create_diskfile`](@ref) which does not use the extended filename parser.
