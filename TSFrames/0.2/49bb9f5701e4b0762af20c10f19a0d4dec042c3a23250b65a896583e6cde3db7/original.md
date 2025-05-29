# Size methods

```julia
nrow(ts::TSFrame)
nr(ts::TSFrame)
```

Return the number of rows of `ts`. `nr` is an alias for `nrow`.

# Examples

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> ts = TSFrame(collect(1:10))
julia> TSFrames.nrow(ts)
10
```
