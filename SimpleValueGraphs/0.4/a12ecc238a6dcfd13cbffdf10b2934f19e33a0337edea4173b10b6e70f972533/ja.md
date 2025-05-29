```
ValDiEdge(s, d[, values])
ValDiEdge{V}(s, d[, values])
ValDiEdge{V, E_VALS}(s, d, values)
```

ソース`s`、デスティネーション`d`、および値`values`を持つ`ValDiEdge`を作成します。

# 例

```jldoctest
julia> e = ValDiEdge(1, 2, ('A',))
ValDiEdge 1 -> 2 with value A

julia> e = ValDiEdge(1, 2, ())
ValDiEdge 1 -> 2

julia> e = ValDiEdge(1,2, (first = 1, second = "2"))
ValDiEdge 1 -> 2 with values (first = 1, second = "2")
```
