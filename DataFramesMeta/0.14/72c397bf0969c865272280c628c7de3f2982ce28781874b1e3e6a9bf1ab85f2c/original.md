```
rdistinct!(d, args...)
```

Row-wise version of `@distinct!`, i.e. all operations use `@byrow` by default. See [`@distinct!`](@ref) for details.

### Examples

```julia
julia> using DataFramesMeta

julia> df = DataFrame(x = 1:5, y = 5:-1:1)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     5
   2 │     2     4
   3 │     3     3
   4 │     4     2
   5 │     5     1
   
julia> @rdistinct!(df, :x + :y)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     5
```
