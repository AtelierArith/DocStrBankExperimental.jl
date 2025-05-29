```
AsTable(cols)
```

A type having a special meaning in `source => transformation => destination` selection operations supported by [`combine`](@ref), [`select`](@ref), [`select!`](@ref), [`transform`](@ref), [`transform!`](@ref), [`subset`](@ref), and [`subset!`](@ref).

If `AsTable(cols)` is used in `source` position it signals that the columns selected by the wrapped selector `cols` should be passed as a `NamedTuple` to the function.

If `AsTable` is used in `destination` position it means that the result of the `transformation` operation is a vector of containers (or a single container if `ByRow(transformation)` is used) that should be expanded  into multiple columns using `keys` to get column names.

# Examples

```jldoctest
julia> df1 = DataFrame(a=1:3, b=11:13)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13

julia> df2 = select(df1, AsTable([:a, :b]) => ByRow(identity))
3×1 DataFrame
 Row │ a_b_identity
     │ NamedTuple…
─────┼─────────────────
   1 │ (a = 1, b = 11)
   2 │ (a = 2, b = 12)
   3 │ (a = 3, b = 13)

julia> select(df2, :a_b_identity => AsTable)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13

julia> select(df1, AsTable([:a, :b]) => ByRow(nt -> map(x -> x^2, nt)) => AsTable)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
```
