```
GeometryEntity{T <: Coordinate}
```

座標系に配置できる幾何学的エンティティ。

新しい具体的な `GeometryEntity` サブタイプは、以下を実装する必要があります：

```julia
to_polygons(::MyEntity)
transform(ent::MyEntity, f)
```

サブタイプは、角度を保持する変換に特別な処理が可能な場合など、`transform(::MyEntity, ::ScaledIsometry)` のような特殊な変換を実装することもできます。また、以下の特殊化も可能です：

```
magnify
rotate
rotate90
reflect_across_xaxis
translate
```

これらは、対応する `ScaledIsometry` を構築し、`transform` を呼び出します。

新しいサブタイプは、`to_polygons`（デフォルト）よりもこれらを計算するためのより良い方法がある場合、以下を実装することもできます：

```julia
footprint
halo
lowerleft
upperright
```

`bounds` によって返される境界矩形は、`lowerleft` と `upperright` から導出されます。デフォルトでは、`halo` は `footprint` と `offset` から導出されます。

新しいサブタイプは、正当なスタイルに必要な任意のアプリケーション関数を実装することもできます。すべてのスタイルが特定のエンティティタイプに対して有効である必要はありません。
