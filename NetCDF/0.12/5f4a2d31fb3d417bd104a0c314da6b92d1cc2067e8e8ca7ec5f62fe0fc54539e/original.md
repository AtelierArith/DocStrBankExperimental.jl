```
nccreate (filename, varname, dimensions ...)
```

Creates a variable in an existing NetCDF file or generates a new file. `filename` and `varname` are strings. After that follows a list of dimensions. Each dimension entry starts with a dimension name (a String), and may be followed by a dimension length, an array with dimension values or a Dict containing dimension attributes. Then the next dimension is entered and so on. Have a look at examples/high.jl for an example use.

### Keyword arguments

  * **atts** Dict of attribute names and values to be assigned to the variable created
  * **gatts** Dict of attribute names and values to be written as global attributes
  * **compress** Integer [0..9] setting the compression level of the file, only valid if `mode=NC_NETCDF4`
  * **t** variable type, currently supported types are: const `NC_BYTE`, `NC_CHAR`, `NC_SHORT`, `NC_INT`, `NC_FLOAT`, `NC_LONG`, `NC_DOUBLE`
  * **mode** file creation mode, only valid when new file is created, choose one of: `NC_NETCDF4`, `NC_CLASSIC_MODEL`, `NC_64BIT_OFFSET`
