# First Row

```julia
first(ts::TSFrame)
```

Returns the first row of `ts` as a TSFrame object.

# Examples

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random)
julia> first(TSFrame(1:10))
(10 x 1) TSFrame with Dates.Date Index

 Index       x1
 Date        Float64
───────────────────────
 2022-02-01  0.768448

```
