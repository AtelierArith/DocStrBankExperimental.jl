```
NcVar
```

`NcVar{T,N,M}` represents a NetCDF variable. It is a subtype of `AbstractArray{T,N}`, so normal indexing using `[]` will work for reading and writing data to and from a NetCDF file. `NcVar` objects are returned by `NetCDF.open`, by indexing an `NcFile` object (e.g. `myfile["temperature"]`) or, when creating a new file, by its constructor. The type parameter `M` denotes the NetCDF data type of the variable, which may or may not correspond to the Julia Data Type.
