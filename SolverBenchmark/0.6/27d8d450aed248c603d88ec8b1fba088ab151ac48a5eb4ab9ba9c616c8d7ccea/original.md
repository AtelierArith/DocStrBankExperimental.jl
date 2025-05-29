```
stats = load_stats(filename; kwargs...)
```

#### Arguments

  * `filename::AbstractString`: the input file name.

#### Keyword arguments

  * `key::String="stats"`: the key under which the data can be read in `filename`. The key should be the same as the one used when `save_stats` was called.

#### Return value

A `Dict{Symbol,DataFrame}` containing the statistics stored in file `filename`. The user should `import DataFrames` before calling `load_stats`.
