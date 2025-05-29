```
fits_create_diskfile(filename::AbstractString)
```

Create and open a new empty output `FITSFile`. Unlike [`fits_create_file`](@ref), this function does not use an extended filename parser and treats the string as is as the filename.
