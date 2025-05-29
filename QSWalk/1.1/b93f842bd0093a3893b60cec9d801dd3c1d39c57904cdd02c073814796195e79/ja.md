```
vertexsetsize(vertexset)
```

与えられた `vertexset` に対応する線形空間の次元を返します。

# 例

```jldoctest; setup = :(using QSWalk)
julia> vertexsetsize(VertexSet([[1, 2, 3], [4, 5]]))
5
```
