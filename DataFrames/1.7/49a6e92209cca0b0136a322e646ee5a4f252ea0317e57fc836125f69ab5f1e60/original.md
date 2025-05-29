```
groupindices(gd::GroupedDataFrame)
```

Return a vector of group indices for each row of `parent(gd)`.

Rows appearing in group `gd[i]` are attributed index `i`. Rows not present in any group are attributed `missing` (this can happen if `skipmissing=true` was passed when creating `gd`, or if `gd` is a subset from a larger [`GroupedDataFrame`](@ref)).

The `groupindices => target_col_name` syntax (or just `groupindices` without specifying the target column name) is also supported in the transformation mini-language when passing a `GroupedDataFrame` to transformation functions ([`combine`](@ref), [`select`](@ref), etc.).

# Examples

```jldoctest
julia> df = DataFrame(id=["a", "c", "b", "b", "a"])
5×1 DataFrame
 Row │ id
     │ String
─────┼────────
   1 │ a
   2 │ c
   3 │ b
   4 │ b
   5 │ a

julia> gdf = groupby(df, :id);

julia> combine(gdf, groupindices)
3×2 DataFrame
 Row │ id      groupindices
     │ String  Int64
─────┼──────────────────────
   1 │ a                  1
   2 │ c                  2
   3 │ b                  3

julia> select(gdf, groupindices => :gid)
5×2 DataFrame
 Row │ id      gid
     │ String  Int64
─────┼───────────────
   1 │ a           1
   2 │ c           2
   3 │ b           3
   4 │ b           3
   5 │ a           1
```
