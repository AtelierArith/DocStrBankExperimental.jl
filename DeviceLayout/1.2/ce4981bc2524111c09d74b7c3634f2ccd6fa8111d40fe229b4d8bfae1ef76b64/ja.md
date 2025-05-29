```
center(geo::AbstractGeometry)
center(geos)
```

境界矩形の中心を返します [`bounds(geo)`](@ref) または `bounds(geos)`。

`geo` が整数座標を持っていても `InexactError` をスローせず、代わりに浮動小数点座標を返します。

関連情報: [`lowerleft`](@ref), [`upperright`](@ref)。
