```
v = variable(ds::NCDataset,varname::String)
```

Return the NetCDF variable `varname` in the dataset `ds` as a `NCDataset.Variable`. No scaling or other transformations are applied when the variable `v` is indexed.
