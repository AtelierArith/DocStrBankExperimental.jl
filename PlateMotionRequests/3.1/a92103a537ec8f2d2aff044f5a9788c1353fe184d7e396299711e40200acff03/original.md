```
write_platemotion(file, table)
```

Write plate motion table to `file` as tab-delimited text columns or NetCDF. The **experimental** NetCDF method will be used if `file` ends with a `.nc` extension. For tab-delimited output, the first line is a header containing the column names.

Throws a `PlateMotionRequests.WriteError` if the table header is not recognised, or if attempting to write a NetCDF file of irregularly sampled data.

!!! note
    Irregular sampling of latitude or longitude values is not supported for NetCDF output.


See also: [`read_platemotion`](@ref).
