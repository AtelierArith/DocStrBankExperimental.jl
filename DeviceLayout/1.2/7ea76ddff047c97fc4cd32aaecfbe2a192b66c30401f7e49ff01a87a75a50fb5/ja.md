```
halo(ent::GeometryEntity{T}, outer_delta, inner_delta=nothing)
```

`ent`の「ハロー」を`outer_delta`のオフセットを使用して返します。

デフォルトでは、ハローは[`offset(footprint(ent), outer_delta)`](@ref)を含むベクターですが、`outer_delta`のマージンで`ent`を完全にカバーする任意の数の`GeometryEntity`を含むことができます。[`footprint(ent)`](@ref)をカバーすることは保証されていません。

`inner_delta`が提供されている場合、結果から`inner_delta`のオフセットが引かれます。

`GeometryEntity`は、ハローの効率的な非`Polygon`表現がある場合、特化した`halo`を実装するべきです。そうでない場合は、デフォルトで`offset`が使用され、最初に`to_polygons`を使用してエンティティを`Polygon`に解決します。
