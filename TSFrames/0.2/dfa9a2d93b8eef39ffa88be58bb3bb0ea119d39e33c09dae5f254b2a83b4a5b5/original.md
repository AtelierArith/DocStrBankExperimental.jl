# Head

```julia
head(ts::TSFrame, n::Int = 10)
```

Returns the first `n` rows of `ts`.

# Examples

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random)
julia> head(TSFrame(1:100))
(10 x 1) TSFrame with Int64 Index

 Index  x1
 Int64  Int64
──────────────
     1      1
     2      2
     3      3
     4      4
     5      5
     6      6
     7      7
     8      8
     9      9
    10     10
```
