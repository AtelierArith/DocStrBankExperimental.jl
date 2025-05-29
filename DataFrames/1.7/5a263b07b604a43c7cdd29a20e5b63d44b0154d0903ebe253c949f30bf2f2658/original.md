```
length(dfr::DataFrameRow)
```

Return the number of elements of `dfr`.

See also: [`size`](@ref)

# Examples

```jldoctest
julia> dfr = DataFrame(a=1:3, b='a':'c')[1, :]
DataFrameRow
 Row │ a      b
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> length(dfr)
2
```
