```
filter(fun, df::AbstractDataFrame; view::Bool=false)
filter(cols => fun, df::AbstractDataFrame; view::Bool=false)
```

Return a data frame containing only rows from `df` for which `fun` returns `true`.

If `cols` is not specified then the predicate `fun` is passed `DataFrameRow`s. Elements of a `DataFrameRow` may be accessed with dot syntax or column indexing inside `fun`.

If `cols` is specified then the predicate `fun` is passed elements of the corresponding columns as separate positional arguments, unless `cols` is an `AsTable` selector, in which case a `NamedTuple` of these arguments is passed. `cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers), and column duplicates are allowed if a vector of `Symbol`s, strings, or integers is passed.

If `view=false` a freshly allocated `DataFrame` is returned. If `view=true` then a `SubDataFrame` view into `df` is returned.

Passing `cols` leads to a more efficient execution of the operation for large data frames.

!!! note
    This method is defined so that DataFrames.jl implements the Julia API for collections, but it is generally recommended to use the [`subset`](@ref) function instead as it is consistent with other DataFrames.jl functions (as opposed to `filter`).


!!! note
    Due to type stability the `filter(cols => fun, df::AbstractDataFrame; view::Bool=false)` call is preferred in performance critical applications.


Metadata: this function preserves table-level and column-level `:note`-style metadata.

See also: [`filter!`](@ref)

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

julia> filter(row -> row.x > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter(row -> row["x"] > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter(:x => x -> x > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter([:x, :y] => (x, y) -> x == 1 || y == "b", df)
3×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     1  b

julia> filter(AsTable(:) => nt -> nt.x == 1 || nt.y == "b", df)
3×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     1  b
```
