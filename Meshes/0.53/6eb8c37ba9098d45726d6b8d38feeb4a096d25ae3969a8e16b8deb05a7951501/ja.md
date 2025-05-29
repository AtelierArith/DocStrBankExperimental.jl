```
PointSet(points)
```

`points`（別名：点群）のセットで、[`Domain`](@ref)を表します。

## 例

以下のすべての点セットは同じで、R³に2つの点を含んでいます：

```julia
julia> PointSet([Point(1,2,3), Point(4,5,6)])
julia> PointSet(Point(1,2,3), Point(4,5,6))
julia> PointSet([(1,2,3), (4,5,6)])
julia> PointSet((1,2,3), (4,5,6))
```
