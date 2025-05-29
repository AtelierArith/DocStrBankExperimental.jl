```
AreaSource(mesh)
```

三角形メッシュに基づいて面照度ソースジオメトリを作成します。

## 例

```jldoctest
julia> using PlantGeomPrimitives

julia> e = Ellipse();

julia> source_geom = AreaSource(e);
```
