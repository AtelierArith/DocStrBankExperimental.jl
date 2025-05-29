```
leaf(surf::ParametricSurface{T}, transform::Transform{T} = identitytransform(T)) -> CSGGenerator{T}
```

与えられた変換を持つパラメトリックサーフェスからリーフノードを作成します。
