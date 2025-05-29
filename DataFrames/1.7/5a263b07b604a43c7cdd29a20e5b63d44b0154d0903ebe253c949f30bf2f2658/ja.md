```
length(dfr::DataFrameRow)
```

`dfr`の要素の数を返します。

参照: [`size`](@ref)

# 例

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
