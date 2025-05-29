```
GeoArray(A::AbstractArray{T,2|3} where T <: NumberOrMissing, f::AffineMap, crs::String)
```

任意の配列と座標を指定する `AffineMap` および WKT 形式の `crs` 文字列から GeoArray を構築します。
