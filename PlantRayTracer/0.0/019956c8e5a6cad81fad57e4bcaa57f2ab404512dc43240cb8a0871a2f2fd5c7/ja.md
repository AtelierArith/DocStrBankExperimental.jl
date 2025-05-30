```
FixedSource(dir)
FixedSource(θ, Φ)
```

与えられた光線の方向ベクトル (dir) または天頂 (θ) および方位 (Φ) 角によって固定された放射源を作成します。

## 例

```jldoctest
julia> source_dir = FixedSource(0.0, 0.0);

julia> import PlantGeomPrimitives as PG

julia> source_dir = FixedSource(PG.Vec(0.0, 0.0, -1.0));
```
