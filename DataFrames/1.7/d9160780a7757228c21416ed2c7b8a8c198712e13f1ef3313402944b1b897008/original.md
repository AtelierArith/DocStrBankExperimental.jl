```
eachcol(df::AbstractDataFrame)
```

Return a `DataFrameColumns` object that is a vector-like that allows iterating an `AbstractDataFrame` column by column.

Indexing into `DataFrameColumns` objects using integer, `Symbol` or string returns the corresponding column (without copying). Indexing into `DataFrameColumns` objects using a multiple column selector returns a subsetted `DataFrameColumns` object with a new parent containing only the selected columns (without copying).

`DataFrameColumns` supports most of the `AbstractVector` API. The key differences are that it is read-only and that the `keys` function returns a vector of `Symbol`s (and not integers as for normal vectors).

In particular `findnext`, `findprev`, `findfirst`, `findlast`, and `findall` functions are supported, and in `findnext` and `findprev` functions it is allowed to pass an integer, string, or `Symbol` as a reference index.

# Examples

```jldoctest
julia> df = DataFrame(x=1:4, y=11:14)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> eachcol(df)
4×2 DataFrameColumns
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> collect(eachcol(df))
2-element Vector{AbstractVector}:
 [1, 2, 3, 4]
 [11, 12, 13, 14]

julia> map(eachcol(df)) do col
           maximum(col) - minimum(col)
       end
2-element Vector{Int64}:
 3
 3

julia> sum.(eachcol(df))
2-element Vector{Int64}:
 10
 50
```
