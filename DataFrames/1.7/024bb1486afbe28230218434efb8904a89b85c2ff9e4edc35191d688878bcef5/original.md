```
subset(df::AbstractDataFrame, args...;
       skipmissing::Bool=false, view::Bool=false, threads::Bool=true)
subset(gdf::GroupedDataFrame, args...;
       skipmissing::Bool=false, view::Bool=false,
       ungroup::Bool=true, threads::Bool=true)
```

Return a copy of data frame `df` or parent of `gdf` containing only rows for which all values produced by transformation(s) `args` for a given row are `true`. All transformations must produce vectors containing `true` or `false`. When the first argument is a `GroupedDataFrame`, transformations are also allowed to return a single `true` or `false` value, which results in including or excluding a whole group.

If `skipmissing=false` (the default) `args` are required to produce results containing only `Bool` values. If `skipmissing=true`, additionally `missing` is allowed and it is treated as `false` (i.e. rows for which one of the conditions returns `missing` are skipped).

Each argument passed in `args` can be any specifier following the rules described for [`select`](@ref) with the restriction that:

  * specifying target column name is not allowed as `subset` does not create new columns;
  * every passed transformation must return a scalar or a vector (returning `AbstractDataFrame`, `NamedTuple`, `DataFrameRow` or `AbstractMatrix` is not supported).

If `view=true` a `SubDataFrame` view  is returned instead of a `DataFrame`.

If `ungroup=false` the resulting data frame is re-grouped based on the same grouping columns as `gdf` and a `GroupedDataFrame` is returned (preserving the order of groups from `gdf`).

If `threads=true` (the default) transformations may be run in separate tasks which can execute in parallel (possibly being applied to multiple rows or groups at the same time). Whether or not tasks are actually spawned and their number are determined automatically. Set to `false` if some transformations require serial execution or are not thread-safe.

If a `GroupedDataFrame` is passed then it must include all groups present in the `parent` data frame, like in [`select!`](@ref).

!!! note
    Note that as the `subset` function works in exactly the same way as other transformation functions defined in DataFrames.jl this is the preferred way to subset rows of a data frame or grouped data frame. In particular it uses a different set of rules for specifying transformations than [`filter`](@ref) which is implemented in DataFrames.jl to ensure support for the standard Julia API for collections.


Metadata: this function preserves table-level and column-level `:note`-style metadata.

See also: [`subset!`](@ref), [`filter`](@ref), [`select`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(id=1:4, x=[true, false, true, false],
                      y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12])
4×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     1   true   true     true      1
   2 │     2  false   true     true      2
   3 │     3   true  false  missing     11
   4 │     4  false  false  missing     12

julia> subset(df, :x)
2×5 DataFrame
 Row │ id     x     y      z        v
     │ Int64  Bool  Bool   Bool?    Int64
─────┼────────────────────────────────────
   1 │     1  true   true     true      1
   2 │     3  true  false  missing     11

julia> subset(df, :v => x -> x .> 3)
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12

julia> subset(df, :x, :y => ByRow(!))
1×5 DataFrame
 Row │ id     x     y      z        v
     │ Int64  Bool  Bool   Bool?    Int64
─────┼────────────────────────────────────
   1 │     3  true  false  missing     11

julia> subset(df, :x, :z, skipmissing=true)
1×5 DataFrame
 Row │ id     x     y     z      v
     │ Int64  Bool  Bool  Bool?  Int64
─────┼─────────────────────────────────
   1 │     1  true  true   true      1

julia> subset(df, :x, :z)
ERROR: ArgumentError: missing was returned in condition number 2 but only true or false are allowed; pass skipmissing=true to skip missing values

julia> subset(groupby(df, :y), :v => x -> x .> minimum(x))
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     2  false   true     true      2
   2 │     4  false  false  missing     12

julia> subset(groupby(df, :y), :v => x -> minimum(x) > 5)
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12
```
