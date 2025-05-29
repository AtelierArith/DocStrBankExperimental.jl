```
offset(ent::GeometryEntity,
    delta;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
offset(ents,
    delta;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
```

境界を `delta` だけ外側にオフセットした結果を含む `Vector` を返します。

エンティティはオフセットする前に [`to_polygons`](@ref) を使用して `Polygon` に解決されます。オフセットは Clipper によって `j` と `e` のオプションを使用して実行されます。

オフセットは特にポリゴン操作であり、Clipper によって実行されます。等価な非ポリゴン `GeometryEntity` を生成する代替メソッド [`halo`](@ref) が定義される場合があります。
