```
trim(layer::SDMLayer, feature::T) where {T <: GeoJSON.GeoJSONT}
```

`GeoJSON`オブジェクトで定義されたフィーチャに従って、レイヤのトリミングされたバージョンを返します。オブジェクトは最初に`feature`に従ってマスクされ、その後トリミングされます。
