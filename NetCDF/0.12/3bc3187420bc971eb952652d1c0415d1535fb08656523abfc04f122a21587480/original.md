```
NcDim(name::String,dimlength::Integer)
```

Creates a NetCDF dimension object named `name` with length `dimlength` in memory.

### Keyword arguments

  * `values=[]` optional for adding dimension values which can be written to a dimension variable
  * `atts` a Dict of attributes associated to the dimension variable
  * `unlimited` is this the record dimension, defaults to `false`
