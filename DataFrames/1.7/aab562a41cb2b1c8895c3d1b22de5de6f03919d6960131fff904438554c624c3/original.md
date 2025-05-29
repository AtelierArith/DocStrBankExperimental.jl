```
nonunique(df::AbstractDataFrame; keep::Symbol=:first)
nonunique(df::AbstractDataFrame, cols; keep::Symbol=:first)
```

Return a `Vector{Bool}` in which `true` entries indicate duplicate rows.

Duplicate rows are those for which at least another row contains equal values (according to `isequal`) for all columns in `cols` (by default, all columns). If `keep=:first` (the default), only the first occurrence of a set of duplicate rows is indicated with a `false` entry. If `keep=:last`, only the last occurrence of a set of duplicate rows is indicated with a `false` entry. If `keep=:noduplicates`, only rows without any duplicates are indicated with a `false` entry.

# Arguments

  * `df` : `AbstractDataFrame`
  * `cols` : a selector specifying the column(s) or their transformations to compare. Can be any column selector or transformation accepted by [`select`](@ref) that returns at least one column if `df` has at least one column.

See also [`unique`](@ref) and [`unique!`](@ref).

# Examples

```jldoctest
julia> df = DataFrame(i=1:4, x=[1, 2, 1, 2])
4×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2

julia> df = vcat(df, df)
8×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2
   5 │     1      1
   6 │     2      2
   7 │     3      1
   8 │     4      2

julia> nonunique(df)
8-element Vector{Bool}:
 0
 0
 0
 0
 1
 1
 1
 1

julia> nonunique(df, keep=:last)
8-element Vector{Bool}:
 1
 1
 1
 1
 0
 0
 0
 0

julia> nonunique(df, 2)
8-element Vector{Bool}:
 0
 0
 1
 1
 1
 1
 1
 1
```
