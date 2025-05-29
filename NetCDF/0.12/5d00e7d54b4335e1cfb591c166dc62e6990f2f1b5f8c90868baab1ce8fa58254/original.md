```
nc_string2char(x::Array{String})
```

Convert a Julia `String` array to an `Array{ASCIIChar}` so that it can be written to a NetCDF variable of type `NC_CHAR`.
