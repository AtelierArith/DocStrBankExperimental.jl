```
readvariable(meta::MetaVLSV, var::String, sorted::Bool=true, usemmap::Bool=false) -> Array
```

Return variable value of `var` from the VLSV file associated with `meta`. By default for DCCRG variables are sorted by cell ID. `usemmap` decides whether to use memory-mapped IO, which is especially useful for large arrays.
