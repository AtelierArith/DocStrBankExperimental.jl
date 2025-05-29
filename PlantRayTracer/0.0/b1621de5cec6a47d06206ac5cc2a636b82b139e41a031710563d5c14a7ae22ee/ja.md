```
Source(geom, angle, power::Number, nrays)
Source(geom, angle, power::Tuple, nrays)
```

ソースジオメトリ、ソース角度、レイごとのパワー、およびこのソースから生成されるレイの総数を指定して、照度ソースを作成します。複数の波長を同時にシミュレーションする場合は、シーンで使用される材料と同じ長さのパワー値のタプルを指定する必要があります。ソースジオメトリとソース角度の詳細については、VPLドキュメントを参照してください。

## 例

```jldoctest
julia> import PlantGeomPrimitives as PG

julia> source_geom = PointSource(PG.O());

julia> source_dir = FixedSource(0.0, 0.0);

julia> Source(source_geom, source_dir, 1.0, 1_000);
```
