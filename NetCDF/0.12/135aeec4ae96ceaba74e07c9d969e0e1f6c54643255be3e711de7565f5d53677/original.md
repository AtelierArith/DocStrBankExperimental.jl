NcDim(name::String,values::AbstractVector)

Creates a NetCDF dimension object named `name` and associated `values` in memory.

### Keyword arguments

  * `atts` a Dict of attributes associated to the dimension variable
  * `unlimited` is this the record dimension, defaults to `false`
