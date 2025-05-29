```
flat_elements(geom::Union{GeometryStructure,GeometryReference}, only_layers=[], ignore_layers=[])
flat_elements(geom_layer::Pair{<:Union{GeometryStructure,GeometryReference}})
```

`GeometryEntity` 要素のリストを flatten(cs) から返し、オプションでメタデータをフィルタリングします。

`only_layers` と `ignore_layers` はレイヤー名 `Symbol`、`DeviceLayout.Meta`、またはそのいずれかのコレクションである可能性があります。メタデータフィルタリング関数は [`layer_inclusion(only_layers, ignore_layers)`](@ref) を使用して生成されます。これは、デフォルトの空の `only_layers` がすべてのレイヤーをリストするのと同じであることを意味します。

引数ペア `geom => layer` を使用することは `flat_elements(geom, layer)` と同等です。 ```
