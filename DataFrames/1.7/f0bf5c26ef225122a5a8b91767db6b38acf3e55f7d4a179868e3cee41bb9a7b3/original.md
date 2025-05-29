```
fillcombinations(df::AbstractDataFrame, indexcols;
                     allowduplicates::Bool=false,
                     fill=missing)
```

Generate all combinations of levels of column(s) `indexcols` in data frame `df`. Levels and their order are determined by the `levels` function (i.e. unique values sorted lexicographically by default, or a custom set of levels for e.g. `CategoricalArray` columns), in addition to `missing` if present.

For combinations of `indexcols` not present in `df` these columns are filled with the `fill` value (`missing` by default).

If `allowduplicates=false` (the default) `indexcols` may only contain unique combinations of `indexcols` values. If `allowduplicates=true` duplicates are allowed.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(x=1:2, y='a':'b', z=["x", "y"])
2×3 DataFrame
 Row │ x      y     z
     │ Int64  Char  String
─────┼─────────────────────
   1 │     1  a     x
   2 │     2  b     y

julia> fillcombinations(df, [:x, :y])
4×3 DataFrame
 Row │ x      y     z
     │ Int64  Char  String?
─────┼──────────────────────
   1 │     1  a     x
   2 │     2  a     missing
   3 │     1  b     missing
   4 │     2  b     y

julia> fillcombinations(df, [:y, :z], fill=0)
4×3 DataFrame
 Row │ x       y     z
     │ Int64?  Char  String
─────┼──────────────────────
   1 │      1  a     x
   2 │      0  b     x
   3 │      0  a     y
   4 │      2  b     y
```
