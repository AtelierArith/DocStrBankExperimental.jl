```
unique!(df::AbstractDataFrame; keep::Symbol=:first)
unique!(df::AbstractDataFrame, cols; keep::Symbol=:first)
```

Update `df` in-place to contain only unique rows.

Non-unique (duplicate) rows are those for which at least another row contains equal values (according to `isequal`) for all columns in `cols` (by default, all columns). If `keep=:first` (the default), only the first occurrence of a set of duplicate rows is kept. If `keep=:last`, only the last occurrence of a set of duplicate rows is kept. If `keep=:noduplicates`, only rows without any duplicates are kept.

# Arguments

  * `df` : the AbstractDataFrame
  * `cols` :  column indicator (`Symbol`, `Int`, `Vector{Symbol}`, `Regex`, etc.) specifying the column(s) to compare. Can be any column selector or transformation accepted by [`select`](@ref) that returns at least one column if `df` has at least one column.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

See also: [`unique!`](@ref), [`nonunique`](@ref).

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

julia> unique!(copy(df))  # modifies df
4×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      1
   4 │     4      2

julia> unique(df, keep=:noduplicates)
0×2 DataFrame
 Row │ i      x
     │ Int64  Int64
─────┴──────────────
```
