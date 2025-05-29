```
GeoArray(A::AbstractArray{T,3} where T <: NumberOrMissing, f::AffineMap)
```

任意の配列と座標を指定する `AffineMap` から GeoArray を構築します。デフォルトの `CRS` が生成されます。
