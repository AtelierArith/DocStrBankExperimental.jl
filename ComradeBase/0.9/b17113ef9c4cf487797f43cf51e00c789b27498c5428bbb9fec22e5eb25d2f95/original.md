```
UnstructuredMap(data::AbstractVector, dims::UnstructuredDomain)
```

A map that is defined on an unstructured domain. This is typically just a vector of values. The vector of locations of the visibilities are stored in `dims`. Otherwise this behaves very similarly to `IntensityMap`, except that is isn't a grid.

For instance the locations of the visibilities can be accessed with `axisdims`, as well as the usual `getproperty` and `propertynames` functions. Like with `IntensityMap` during execution the `executor` is used to determine the execution context.
