```
intersect2d(p1, p2)
```

`p1`の幾何学的和と`p2`の幾何学的和の交差を`ClippedPolygon`として返します。

`p1`と`p2`のそれぞれは`GeometryEntity`または`GeometryEntity`の配列である可能性があります。すべてのエンティティは最初に[`to_polygons`](@ref)を使用してポリゴンに変換されます。

`p1`と`p2`のそれぞれは`GeometryStructure`または`GeometryReference`でもあり得る場合、その場合は`elements(flatten(p))`がポリゴンに変換されます。

それぞれは`geom => layer`のペアでもあり得ます。ここで`geom`は`GeometryStructure`または`GeometryReference`であり、`layer`は`DeviceLayout.Meta`、レイヤー名`Symbol`、および/またはそれらのコレクションであり、その場合はそのレイヤー内の要素のみが使用されます。
