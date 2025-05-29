```
rownumber(dfr::DataFrameRow)
```

Return a row number in the `AbstractDataFrame` that `dfr` was created from.

Note that this differs from the first element in the tuple returned by `parentindices`. The latter gives the row number in the `parent(dfr)`, which is the source `DataFrame` where data that `dfr` gives access to is stored.

# Examples

```jldoctest
julia> df = DataFrame(reshape(1:12, 3, 4), :auto)
3×4 DataFrame
 Row │ x1     x2     x3     x4
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      4      7     10
   2 │     2      5      8     11
   3 │     3      6      9     12

julia> dfr = df[2, :]
DataFrameRow
 Row │ x1     x2     x3     x4
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   2 │     2      5      8     11

julia> rownumber(dfr)
2

julia> parentindices(dfr)
(2, Base.OneTo(4))

julia> parent(dfr)
3×4 DataFrame
 Row │ x1     x2     x3     x4
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      4      7     10
   2 │     2      5      8     11
   3 │     3      6      9     12

julia> dfv = @view df[2:3, 1:3]
2×3 SubDataFrame
 Row │ x1     x2     x3
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     2      5      8
   2 │     3      6      9

julia> dfrv = dfv[2, :]
DataFrameRow
 Row │ x1     x2     x3
     │ Int64  Int64  Int64
─────┼─────────────────────
   3 │     3      6      9

julia> rownumber(dfrv)
2

julia> parentindices(dfrv)
(3, 1:3)

julia> parent(dfrv)
3×4 DataFrame
 Row │ x1     x2     x3     x4
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      4      7     10
   2 │     2      5      8     11
   3 │     3      6      9     12
```
