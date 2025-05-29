```
FileIndex(grib_path::String; index_keys = ALL_KEYS, filter_by_values = Dict())
```

Construct a [`FileIndex`](@ref) for the file `grib_path`, storing only the keys in `index_keys`. It is possible to read only specific values by specifying them in `filter_by_values`. The values of the headers can be accessed with `getindex`.
