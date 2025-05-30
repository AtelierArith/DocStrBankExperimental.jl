```
LineSource(p, line)
```

原点（`p`）とセグメント（`line`）を指定された直線放射源ジオメトリを作成します。両方ともデカルト座標のベクトル（`Vec(x, y, z)`）として指定されます。これにより、点 `p` と `p .+ line` の間に直線源が作成されます。

## 例

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = LineSource(PG.Vec(1.0, 1.0, 1.0), PG.Y());
```
