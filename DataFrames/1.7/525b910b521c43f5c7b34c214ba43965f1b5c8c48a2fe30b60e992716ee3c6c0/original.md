```
proprow
```

Compute the proportion of rows which belong to each group, i.e. its number of rows divided by the total number of rows in a `GroupedDataFrame`.

This function can only be used in the transformation mini-language via the `proprow => target_col_name` syntax (or just `proprow` without specifying the target column name), when passing a `GroupedDataFrame` to transformation functions ([`combine`](@ref), [`select`](@ref), etc.).

# Examples

```jldoctest
julia> df = DataFrame(id=["a", "c", "b", "b", "a", "b"])
6×1 DataFrame
 Row │ id
     │ String
─────┼────────
   1 │ a
   2 │ c
   3 │ b
   4 │ b
   5 │ a
   6 │ b

julia> gdf = groupby(df, :id);

julia> combine(gdf, proprow)
3×2 DataFrame
 Row │ id      proprow
     │ String  Float64
─────┼──────────────────
   1 │ a       0.333333
   2 │ c       0.166667
   3 │ b       0.5

julia> select(gdf, proprow => :frac)
6×2 DataFrame
 Row │ id      frac
     │ String  Float64
─────┼──────────────────
   1 │ a       0.333333
   2 │ c       0.166667
   3 │ b       0.5
   4 │ b       0.5
   5 │ a       0.333333
   6 │ b       0.5
```
