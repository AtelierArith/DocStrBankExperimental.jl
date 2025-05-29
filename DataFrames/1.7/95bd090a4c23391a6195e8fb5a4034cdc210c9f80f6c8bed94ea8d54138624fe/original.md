```
sort(df::AbstractDataFrame, cols=All();
     alg::Union{Algorithm, Nothing}=nothing,
     lt::Union{Function, AbstractVector{<:Function}}=isless,
     by::Union{Function, AbstractVector{<:Function}}=identity,
     rev::Union{Bool, AbstractVector{Bool}}=false,
     order::Union{Ordering, AbstractVector{<:Ordering}}=Forward,
     view::Bool=false,
     checkunique::Bool=false)
```

Return a data frame containing the rows in `df` sorted by column(s) `cols`. Sorting on multiple columns is done lexicographically.

`cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers). If `cols` selects no columns, sort `df` on all columns (this behaviour is deprecated and will change in future versions).

If `rev` is `true`, reverse sorting is performed. To enable reverse sorting only for some columns, pass `order(c, rev=true)` in `cols`, with `c` the corresponding column index (see example below).

Since having repeated elements makes multiple sorting orders valid, the `checkunique` keyword allows for the situation to be caught. If `checkunique` is `true` and duplicate elements are found an error will be thrown. The use of the `checkunique` keyword is only supported when neither the `by` nor the `lt` keywords are being used. Similarly, the use of `order(...)` clauses that specify either `by` or `lt` are not supported, but specifying `rev` by itself is allowed.

The `by` keyword allows providing a function that will be applied to each cell before comparison; the `lt` keyword allows providing a custom "less than" function. If both `by` and `lt` are specified, the `lt` function is applied to the result of the `by` function.

Keyword arguments specifying sorting order (`rev`, `lt` or `by`) can either be a single value, or a vector of length equal to the number of columns the operation is performed on. When a single value is passed, it applies to all columns. When a vector is passed, each entry applies to the column in the corresponding position in `cols`.

If `alg` is `nothing` (the default), the most appropriate algorithm is chosen automatically among `TimSort`, `MergeSort` and `RadixSort` depending on the type of the sorting columns and on the number of rows in `df`.

If `view=false` a freshly allocated `DataFrame` is returned. If `view=true` then a `SubDataFrame` view into `df` is returned.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

# Examples

```jldoctest
julia> df = DataFrame(x=[3, 1, 2, 1], y=["b", "c", "a", "b"])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     2  a
   4 │     1  b

julia> sort(df, :x)
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  c
   2 │     1  b
   3 │     2  a
   4 │     3  b

julia> sort(df, [:x, :y])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  b
   2 │     1  c
   3 │     2  a
   4 │     3  b

julia> sort(df, [:x, :y], rev=true)
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a
   3 │     1  c
   4 │     1  b

julia> sort(df, [:x, order(:y, rev=true)])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     1  c
   2 │     1  b
   3 │     2  a
   4 │     3  b
```
