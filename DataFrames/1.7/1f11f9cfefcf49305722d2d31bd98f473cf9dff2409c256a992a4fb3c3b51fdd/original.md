```
filter(fun, gdf::GroupedDataFrame; ungroup::Bool=false)
filter(cols => fun, gdf::GroupedDataFrame; ungroup::Bool=false)
```

Return only groups in `gd` for which `fun` returns `true` as a `GroupedDataFrame` if `ungroup=false` (the default), or as a data frame if `ungroup=true`.

If `cols` is not specified then the predicate `fun` is called with a `SubDataFrame` for each group.

If `cols` is specified then the predicate `fun` is called for each group with views of the corresponding columns as separate positional arguments, unless `cols` is an `AsTable` selector, in which case a `NamedTuple` of these arguments is passed. `cols` can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers), and column duplicates are allowed if a vector of `Symbol`s, strings, or integers is passed.

!!! note
    This method is defined so that DataFrames.jl implements the Julia API for collections, but it is generally recommended to use the [`subset`](@ref) function instead as it is consistent with other DataFrames.jl functions (as opposed to `filter`).


# Examples

```jldoctest
julia> df = DataFrame(g=[1, 2], x=['a', 'b']);

julia> gd = groupby(df, :g)
GroupedDataFrame with 2 groups based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a
⋮
Last Group (1 row): g = 2
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     2  b

julia> filter(x -> x.x[1] == 'a', gd)
GroupedDataFrame with 1 group based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> filter(:x => x -> x[1] == 'a', gd)
GroupedDataFrame with 1 group based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> filter(:x => x -> x[1] == 'a', gd, ungroup=true)
1×2 DataFrame
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a
```
