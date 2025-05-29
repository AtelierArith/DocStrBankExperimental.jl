```
var = getindex(ds::Union{AbstractDataset,AbstractVariable},cfname::CFStdName)
```

Return the NetCDF variable `var` with the standard name `cfname` from a dataset. If the first argument is a variable, then the search is limited to all variables with the same dimension names.
