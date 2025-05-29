```
union2d(p1, p2)
```

p1とp2の幾何学的和を`ClippedPolygon`として返します。

p1とp2のそれぞれは`GeometryEntity`または`GeometryEntity`の配列である可能性があります。すべてのエンティティは最初に[`to_polygons`](@ref)を使用してポリゴンに変換されます。

p1とp2のそれぞれは`GeometryStructure`または`GeometryReference`でもあり得ます。この場合、`elements(flatten(p))`はポリゴンに変換されます。

それぞれは`geom => layer`のペアでもあり得ます。この場合、`geom`は`GeometryStructure`または`GeometryReference`であり、`layer`は`DeviceLayout.Meta`、レイヤー名`Symbol`、またはそのいずれかのコレクションであり、この場合はそのレイヤー内の要素のみが使用されます。

これは`union`のメソッドとして実装されていないのは、ポリゴンの配列の集合和を持つことができ、これは異なる操作だからです。

ClipperポリフィルルールはPolyFillTypePositiveであり、これは領域がより多くの非ホール（向きによる）ポリゴンの中にある限り、和の中にあることを意味します。
