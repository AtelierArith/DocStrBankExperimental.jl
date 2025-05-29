```
ValEdge(s, d[, values])
ValEdge{V}(s, d[, values])
ValEdge{V, E_VALS}(s, d, values)
```

ソース`s`、宛先`d`、および値`values`を持つ`ValEdge`を作成します。

# 例

```jldoctest
julia> e = ValEdge(1, 2, ('A',))
ValEdge 1 -- 2 with value A

julia> e = ValEdge(1, 2, ())
ValEdge 1 -- 2

julia> e = ValEdge(1,2, (first = 1, second = "2"))
ValEdge 1 -- 2 with values (first = 1, second = "2")
```
