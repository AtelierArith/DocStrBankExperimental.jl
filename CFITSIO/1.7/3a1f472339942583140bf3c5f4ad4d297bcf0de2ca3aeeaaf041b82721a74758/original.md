```
fits_read_atblhdr(f::FITSFile, maxdim::Integer = 99)
```

Read the header of an ASCII table HDU, where `maxdim` represents the maximum number of columns to read. The function returns the length of a row in bytes, the number of rows, the number of columns, the column names as a `Vector{String}`, the byte offsets to each column, the TFORMn values as a `Vector{String}`, the TUNITn values as a `Vector{String}`, and the `EXTNAME::String` keyword, if any.
