```
size(dfr::DataFrameRow[, dim])
```

Return a 1-tuple containing the number of elements of `dfr`. If an optional dimension `dim` is specified, it must be `1`, and the number of elements is returned directly as a number.

See also: [`length`](@ref)

# Examples

```jldoctest
julia> dfr = DataFrame(a=1:3, b='a':'c')[1, :]
DataFrameRow
 Row │ a      b
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> size(dfr)
(2,)

julia> size(dfr, 1)
2
```
