```
append!(df::DataFrame, tables...; cols::Symbol=:setequal,
        promote::Bool=(cols in [:union, :subset]))
```

Add the rows of tables passed as `tables` to the end of `df`. If the table is not an `AbstractDataFrame` then it is converted using `DataFrame(table, copycols=false)` before being appended.

The exact behavior of `append!` depends on the `cols` argument:

  * If `cols == :setequal` (this is the default) then `df2` must contain exactly the same columns as `df` (but possibly in a different order).
  * If `cols == :orderequal` then `df2` must contain the same columns in the same order (for `AbstractDict` this option requires that `keys(row)` matches `propertynames(df)` to allow for support of ordered dicts; however, if `df2` is a `Dict` an error is thrown as it is an unordered collection).
  * If `cols == :intersect` then `df2` may contain more columns than `df`, but all column names that are present in `df` must be present in `df2` and only these are used.
  * If `cols == :subset` then `append!` behaves like for `:intersect` but if some column is missing in `df2` then a `missing` value is pushed to `df`.
  * If `cols == :union` then `append!` adds columns missing in `df` that are present in `df2`, for columns present in `df` but missing in `df2` a `missing` value is pushed.

If `promote=true` and element type of a column present in `df` does not allow the type of a pushed argument then a new column with a promoted element type allowing it is freshly allocated and stored in `df`. If `promote=false` an error is thrown.

The above rule has the following exceptions:

  * If `df` has no columns then copies of columns from `df2` are added to it.
  * If `df2` has no columns then calling `append!` leaves `df` unchanged.

Please note that `append!` must not be used on a `DataFrame` that contains columns that are aliases (equal when compared with `===`).

Metadata: table-level `:note`-style metadata and column-level `:note`-style metadata for columns present in `df` are preserved. If new columns are added their `:note`-style metadata is copied from the appended table. Other metadata is dropped.

See also: use [`push!`](@ref) to add individual rows to a data frame, [`prepend!`](@ref) to add a table at the beginning, and [`vcat`](@ref) to vertically concatenate data frames.

# Examples

```jldoctest
julia> df1 = DataFrame(A=1:3, B=1:3)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> df2 = DataFrame(A=4.0:6.0, B=4:6)
3×2 DataFrame
 Row │ A        B
     │ Float64  Int64
─────┼────────────────
   1 │     4.0      4
   2 │     5.0      5
   3 │     6.0      6

julia> append!(df1, df2);

julia> df1
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

julia> append!(df2, DataFrame(A=1), (; C=1:2), cols=:union)
6×3 DataFrame
 Row │ A          B        C
     │ Float64?   Int64?   Int64?
─────┼─────────────────────────────
   1 │       4.0        4  missing
   2 │       5.0        5  missing
   3 │       6.0        6  missing
   4 │       1.0  missing  missing
   5 │ missing    missing        1
   6 │ missing    missing        2
```
