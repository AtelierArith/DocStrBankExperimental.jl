```
zone(layer::SDMLayer, polygons::Vector{T}) where {T <: Union{Polygon,MultiPolygon,Feature,FeatureCollection}}
```

ポリゴンに属する各ピクセルの値がそのポリゴンのインデックスに設定されたレイヤーを返します。最初に値が設定されたがポリゴンの一部ではないセルはオフにされます。
