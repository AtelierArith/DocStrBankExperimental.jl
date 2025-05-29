```
size(dfr::DataFrameRow[, dim])
```

`dfr`の要素数を含む1タプルを返します。オプションの次元`dim`が指定されている場合、それは`1`でなければならず、要素数は数値として直接返されます。

参照: [`length`](@ref)

# 例

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
