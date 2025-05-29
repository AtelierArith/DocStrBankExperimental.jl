```
SimpleSDMLayers.mask!(layer::SDMLayer, poly::T) where T<:Union{Polygon,MultiPolygon}
```

ポリゴンの外側（またはポリゴン内の穴の中）にあるすべてのセルをオフにします。これはオブジェクトを変更します。
