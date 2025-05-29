# Size methods

```julia
size(ts::TSFrame)
```

Return the number of rows and columns of `ts` as a tuple.

# Examples

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> TSFrames.size(TSFrame([collect(1:100) collect(1:100) collect(1:100)]))
(100, 3)
```
