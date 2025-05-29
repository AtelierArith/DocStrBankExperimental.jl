```
shannon!(abt::AbstractAbundanceTable; overwrite=false)
```

Adds a `:shannon` entry to the metadata for each sample in `abt` with the Shannon alpha diversity of that sample (see [`shannon`](@ref)). If `overwrite=false` (the default), uses `insert!` to perform this operation, so an error will be thrown if any sample already contains a `:shannon` entry. Otherwise, uses `set!`.
