```
ginisimpson!(abt::AbstractAbundanceTable; overwrite=false)
```

Adds a `:ginisimpson` entry to the metadata for each sample in `abt` with the Gini-Simpson alpha diversity of that sample (see [`ginisimpson`](@ref)). If `overwrite=false` (the default), uses `insert!` to perform this operation, so an error will be thrown if any sample already contains a `:ginisimpson` entry. Otherwise, uses `set!`.
