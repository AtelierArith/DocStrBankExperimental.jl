```
save_stats(stats, filename; kwargs...)
```

Write the benchmark statistics `stats` to a file named `filename`.

#### Arguments

  * `stats::Dict{Symbol,DataFrame}`: benchmark statistics such as returned by `bmark_solvers`
  * `filename::AbstractString`: the output file name.

#### Keyword arguments

  * `force::Bool=false`: whether to overwrite `filename` if it already exists
  * `key::String="stats"`: the key under which the data can be read from `filename` later.

#### Return value

This method returns an error if `filename` exists and `force==false`. On success, it returns the value of `jldopen(filename, "w")`.
