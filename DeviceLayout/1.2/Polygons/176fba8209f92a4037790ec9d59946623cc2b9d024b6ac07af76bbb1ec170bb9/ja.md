```
difference2d(p1, p2)
```

`p1`の幾何学的和から`p2`の幾何学的和を引いた結果を`ClippedPolygon`として返します。

`p1`と`p2`のそれぞれは`GeometryEntity`または`GeometryEntity`の配列である可能性があります。すべてのエンティティは最初に[`to_polygons`](@ref)を使用してポリゴンに変換されます。

`p1`と`p2`のそれぞれは`GeometryStructure`または`GeometryReference`でもあり得ます。この場合、`elements(flatten(p))`はポリゴンに変換されます。

それぞれは`geom => layer`のペアでもあり得ます。この場合、`geom`は`GeometryStructure`または`GeometryReference`であり、`layer`は`DeviceLayout.Meta`、レイヤー名`Symbol`、および/またはそれらのコレクションであり、この場合はそのレイヤー内の要素のみが使用されます。
