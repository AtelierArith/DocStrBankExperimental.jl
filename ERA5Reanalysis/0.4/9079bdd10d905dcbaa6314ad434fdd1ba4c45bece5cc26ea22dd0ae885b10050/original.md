```
ERA5Daily <: ERA5Custom
```

Specifies that the dataset to be analyzed contains hourly data.  All fields are the same as that specified in the `ERA5Dataset` docstring.  However, the fields `sldoi`, `pldoi` and `ptype` are all set to `N/A` because `ERA5Daily` is not available in, nor downloadable from, the Climate Data Store.
