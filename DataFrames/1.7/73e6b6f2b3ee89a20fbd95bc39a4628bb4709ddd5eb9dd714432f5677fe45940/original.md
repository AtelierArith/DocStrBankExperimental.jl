```
subset!(df::AbstractDataFrame, args...;
        skipmissing::Bool=false, threads::Bool=true)
subset!(gdf::GroupedDataFrame{DataFrame}, args...;
        skipmissing::Bool=false, ungroup::Bool=true, threads::Bool=true)
```

Update data frame `df` or the parent of `gdf` in place to contain only rows for which all values produced by transformation(s) `args` for a given row is `true`. All transformations must produce vectors containing `true` or `false`. When the first argument is a `GroupedDataFrame`, transformations are also allowed to return a single `true` or `false` value, which results in including or excluding a whole group.

If `skipmissing=false` (the default) `args` are required to produce results containing only `Bool` values. If `skipmissing=true`, additionally `missing` is allowed and it is treated as `false` (i.e. rows for which one of the conditions returns `missing` are skipped).

Each argument passed in `args` can be any specifier following the rules described for [`select`](@ref) with the restriction that:

  * specifying target column name is not allowed as `subset!` does not create new columns;
  * every passed transformation must return a scalar or a vector (returning `AbstractDataFrame`, `NamedTuple`, `DataFrameRow` or `AbstractMatrix` is not supported).

If `ungroup=false` the passed `GroupedDataFrame` `gdf` is updated (preserving the order of its groups) and returned.

If `threads=true` (the default) transformations may be run in separate tasks which can execute in parallel (possibly being applied to multiple rows or groups at the same time). Whether or not tasks are actually spawned and their number are determined automatically. Set to `false` if some transformations require serial execution or are not thread-safe.

If `GroupedDataFrame` is subsetted then it must include all groups present in the `parent` data frame, like in [`select!`](@ref). In this case the passed `GroupedDataFrame` is updated to have correct groups after its parent is updated.

!!! note
    Note that as the `subset!` function works in exactly the same way as other transformation functions defined in DataFrames.jl this is the preferred way to subset rows of a data frame or grouped data frame. In particular it uses a different set of rules for specifying transformations than [`filter!`](@ref) which is implemented in DataFrames.jl to ensure support for the standard Julia API for collections.


Metadata: this function preserves table-level and column-level `:note`-style metadata.

See also: [`subset`](@ref), [`filter!`](@ref), [`select!`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false])
4×3 DataFrame
 Row │ id     x      y
     │ Int64  Bool   Bool
─────┼─────────────────────
   1 │     1   true   true
   2 │     2  false   true
   3 │     3   true  false
   4 │     4  false  false

julia> subset!(df, :x, :y => ByRow(!));

julia> df
1×3 DataFrame
 Row │ id     x     y
     │ Int64  Bool  Bool
─────┼────────────────────
   1 │     3  true  false

julia> df = DataFrame(id=1:4, y=[true, true, false, false], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> x .> minimum(x));

julia> df
2×3 DataFrame
 Row │ id     y      v
     │ Int64  Bool   Int64
─────┼─────────────────────
   1 │     2   true      2
   2 │     4  false     12

julia> df = DataFrame(id=1:4, x=[true, false, true, false],
                      z=[true, true, missing, missing], v=1:4)
4×4 DataFrame
 Row │ id     x      z        v
     │ Int64  Bool   Bool?    Int64
─────┼──────────────────────────────
   1 │     1   true     true      1
   2 │     2  false     true      2
   3 │     3   true  missing      3
   4 │     4  false  missing      4

julia> subset!(df, :x, :z)
ERROR: ArgumentError: missing was returned in condition number 2 but only true or false are allowed; pass skipmissing=true to skip missing values

julia> subset!(df, :x, :z, skipmissing=true);

julia> df
1×4 DataFrame
 Row │ id     x     z      v
     │ Int64  Bool  Bool?  Int64
─────┼───────────────────────────
   1 │     1  true   true      1

julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> x .> minimum(x));

julia> df
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     2  false   true     true      2
   2 │     4  false  false  missing     12

julia> df = DataFrame(id=1:4, x=[true, false, true, false], y=[true, true, false, false],
                      z=[true, true, missing, missing], v=[1, 2, 11, 12]);

julia> subset!(groupby(df, :y), :v => x -> minimum(x) > 5);

julia> df
2×5 DataFrame
 Row │ id     x      y      z        v
     │ Int64  Bool   Bool   Bool?    Int64
─────┼─────────────────────────────────────
   1 │     3   true  false  missing     11
   2 │     4  false  false  missing     12
```
