```
PointSource(vec)
```

指定された3D位置`vec`に点放射源ジオメトリを作成します。これはデカルト座標のベクトル（`Vec(x, y, z)`）として定義されます。

## 例

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = PointSource(PG.Vec(1.0, 1.0, 1.0));
```
