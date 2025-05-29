```
completecases(df::AbstractDataFrame, cols=:)
```

Return a Boolean vector with `true` entries indicating rows without missing values (complete cases) in data frame `df`.

If `cols` is provided, only missing values in the corresponding columns are considered. `cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers) that returns at least one column if `df` has at least one column.

See also: [`dropmissing`](@ref) and [`dropmissing!`](@ref). Use `findall(completecases(df))` to get the indices of the rows.

# Examples

```jldoctest
julia> df = DataFrame(i=1:5,
                      x=[missing, 4, missing, 2, 1],
                      y=[missing, missing, "c", "d", "e"])
5×3 DataFrame
 Row │ i      x        y
     │ Int64  Int64?   String?
─────┼─────────────────────────
   1 │     1  missing  missing
   2 │     2        4  missing
   3 │     3  missing  c
   4 │     4        2  d
   5 │     5        1  e

julia> completecases(df)
5-element BitVector:
 0
 0
 0
 1
 1

julia> completecases(df, :x)
5-element BitVector:
 0
 1
 0
 1
 1

julia> completecases(df, [:x, :y])
5-element BitVector:
 0
 0
 0
 1
 1
```
