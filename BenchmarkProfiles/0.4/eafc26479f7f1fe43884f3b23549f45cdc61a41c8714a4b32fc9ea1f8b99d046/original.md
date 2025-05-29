```
performance_profile(b, T, labels; logscale=true, title="", sampletol=0.0, drawtol=0.0; kwargs...)
```

Produce a performance profile using the specified backend.

## Arguments

  * `b :: AbstractBackend`: the backend used to produce the plot.
  * `T :: Matrix{<: Number}`: each column of `T` defines the performance data for a solver (positive, and smaller is better). Failures on a given problem are represented by a negative value, an infinite value, or `NaN`.
  * `labels :: Vector{AbstractString}`: a vector of labels for each profile used to produce a legend. If empty, `labels` will be set to `["column 1", "column 2", ...]`.

## Keyword Arguments

  * `logscale :: Bool=true`: produce a logarithmic (base 2) performance plot.
  * `title :: AbstractString=""`: set a title for the plot.
  * `sampletol :: Float64 = 0.0`: a tolerance used to downsample profiles for performance when using a large number of problems.
  * `drawtol :: Float64 = 0.0`: a tolerance to declare a draw between two performance measures.
  * `linestyles::Vector{Symbol}`: a vector of line styles to use for the profiles, if supported by the backend.

Other keyword arguments are passed to the plot command for the corresponding backend.
