```
readvariable(meta::MetaVLSV, var::String, ids::Vector{Int}) -> Array
```

Read variable `var` in a collection of cells `ids` associated with `meta`. if `ids` is empty, return the whole sorted array of `var`.
