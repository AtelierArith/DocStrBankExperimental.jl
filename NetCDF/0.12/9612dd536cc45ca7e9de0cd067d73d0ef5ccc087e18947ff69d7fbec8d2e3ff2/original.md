```
NcVar(name::AbstractString,dimin::Union{NcDim,Array{NcDim,1}}
```

Creates a new NetCDF variable `name` in memory. The variable is associated to a list of NetCDF dimensions specified by `dimin`.

### Keyword arguments

  * `atts` Dictionary representing the variables attributes
  * `t` either a Julia type, (one of `Int16`, `Int32`, `Float32`, `Float64`, `String`) or a NetCDF data type (`NC_SHORT`, `NC_INT`, `NC_FLOAT`, `NC_DOUBLE`, `NC_CHAR`, `NC_STRING`) determines the data type of the variable. Defaults to -1
  * `compress` Integer which sets the compression level of the variable for NetCDF4 files. Defaults to -1 (no compression). Compression levels of 1..9 are valid
