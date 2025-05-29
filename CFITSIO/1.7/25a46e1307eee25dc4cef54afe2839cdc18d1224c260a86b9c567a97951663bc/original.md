```
fits_read_btblhdr(f::FITSFile, maxdim::Integer = 99)
```

Read the header of a binary table HDU, where `maxdim` represents the maximum number of columns to read. The function returns the number of rows, the number of columns, the column names as a `Vector{String}`, the TFORMn values  as a `Vector{String}`, the TUNITn values as a `Vector{String}`, and the `EXTNAME::String` and `PCOUNT::Int` keywords.
