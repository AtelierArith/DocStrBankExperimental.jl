```
addstyle!(d::StyleDict, s::GeometryEntityStyle, indices::Vector{Int})
addstyle!(d::StyleDict, s::GeometryEntityStyle, indices::Int...)
addstyle!(d::StyleDict, s::GeometryEntityStyle, node::Clipper.PolyNode)
```

Insert a `GeometryEntityStyle` into a `StyleDict` at location specified by `indices` or by a particular `node` in the tree defined by a `ClippedPolygon`.
