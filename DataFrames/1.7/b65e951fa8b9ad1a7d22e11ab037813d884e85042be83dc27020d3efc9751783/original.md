```
vcat(dfs::AbstractDataFrame...;
     cols::Union{Symbol, AbstractVector{Symbol},
                 AbstractVector{<:AbstractString}}=:setequal,
     source::Union{Nothing, Symbol, AbstractString,
                   Pair{<:Union{Symbol, AbstractString}, <:AbstractVector}}=nothing)
```

Vertically concatenate `AbstractDataFrame`s.

The `cols` keyword argument determines the columns of the returned data frame:

  * `:setequal`: require all data frames to have the same column names disregarding order. If they appear in different orders, the order of the first provided data frame is used.
  * `:orderequal`: require all data frames to have the same column names and in the same order.
  * `:intersect`: only the columns present in *all* provided data frames are kept. If the intersection is empty, an empty data frame is returned.
  * `:union`: columns present in *at least one* of the provided data frames are kept. Columns not present in some data frames are filled with `missing` where necessary.
  * A vector of `Symbol`s or strings: only listed columns are kept. Columns not present in some data frames are filled with `missing` where necessary.

The `source` keyword argument, if not `nothing` (the default), specifies the additional column to be added in the last position in the resulting data frame that will identify the source data frame. It can be a `Symbol` or an `AbstractString`, in which case the identifier will be the number of the passed source data frame, or a `Pair` consisting of a `Symbol` or an `AbstractString` and of a vector specifying the data frame identifiers (which do not have to be unique). The name of the source column is not allowed to be present in any source data frame.

The order of columns is determined by the order they appear in the included data frames, searching through the header of the first data frame, then the second, etc.

The element types of columns are determined using `promote_type`, as with `vcat` for `AbstractVector`s.

`vcat` ignores empty data frames when composing the result (except for metadata), making it possible to initialize an empty data frame at the beginning of a loop and `vcat` onto it.

Metadata: `vcat` propagates table-level `:note`-style metadata for keys that are present in all passed data frames and have the same value. `vcat` propagates column-level `:note`-style metadata for keys that are present in all passed data frames that contain this column and have the same value.

# Example

```jldoctest
julia> df1 = DataFrame(A=1:3, B=1:3)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> df2 = DataFrame(A=4:6, B=4:6)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     4      4
   2 │     5      5
   3 │     6      6

julia> df3 = DataFrame(A=7:9, C=7:9)
3×2 DataFrame
 Row │ A      C
     │ Int64  Int64
─────┼──────────────
   1 │     7      7
   2 │     8      8
   3 │     9      9

julia> df4 = DataFrame()
0×0 DataFrame

julia> vcat(df1, df2)
6×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      5
   6 │     6      6

julia> vcat(df1, df3, cols=:union)
6×3 DataFrame
 Row │ A      B        C
     │ Int64  Int64?   Int64?
─────┼─────────────────────────
   1 │     1        1  missing
   2 │     2        2  missing
   3 │     3        3  missing
   4 │     7  missing        7
   5 │     8  missing        8
   6 │     9  missing        9

julia> vcat(df1, df3, cols=:intersect)
6×1 DataFrame
 Row │ A
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     7
   5 │     8
   6 │     9

julia> vcat(df4, df1)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> vcat(df1, df2, df3, df4, cols=:union, source="source")
9×4 DataFrame
 Row │ A      B        C        source
     │ Int64  Int64?   Int64?   Int64
─────┼─────────────────────────────────
   1 │     1        1  missing       1
   2 │     2        2  missing       1
   3 │     3        3  missing       1
   4 │     4        4  missing       2
   5 │     5        5  missing       2
   6 │     6        6  missing       2
   7 │     7  missing        7       3
   8 │     8  missing        8       3
   9 │     9  missing        9       3

julia> vcat(df1, df2, df4, df3, cols=:union, source=:source => 'a':'d')
9×4 DataFrame
 Row │ A      B        C        source
     │ Int64  Int64?   Int64?   Char
─────┼─────────────────────────────────
   1 │     1        1  missing  a
   2 │     2        2  missing  a
   3 │     3        3  missing  a
   4 │     4        4  missing  b
   5 │     5        5  missing  b
   6 │     6        6  missing  b
   7 │     7  missing        7  d
   8 │     8  missing        8  d
   9 │     9  missing        9  d
```
