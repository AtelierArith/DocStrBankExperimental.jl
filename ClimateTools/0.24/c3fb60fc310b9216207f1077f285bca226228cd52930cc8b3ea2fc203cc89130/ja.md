```
shapefile_coords_poly(poly::Shapefile.Polygon)
```

shp.shapes[i] に含まれるポリゴンを返します。ポリゴンを含む配列を返します。

ベクトルではなく配列を返す [`shapefile_coords`](@ref) も参照してください。返されるポリゴンは、[`load`](@ref) 関数のデータ抽出と一貫しています。
