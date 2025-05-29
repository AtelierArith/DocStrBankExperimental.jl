```
to_polygons(ent::GeometryEntity; kwargs...)
```

単一のポリゴン、イテレータ、または `ent` に相当する `Polygon` の `Vector` を返します。

`ent` が `StyledEntity` の場合、ポリゴンへの変換前にすべてのスタイルが適用されます。
