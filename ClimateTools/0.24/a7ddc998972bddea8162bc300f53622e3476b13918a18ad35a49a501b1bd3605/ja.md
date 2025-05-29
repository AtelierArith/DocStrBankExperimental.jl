```
shapefile_coords(poly::Shapefile.Polygon)
```

この関数は、shp.shapes[i] に含まれるポリゴンを返します。x および y 座標ベクトルを返します。

また、データ抽出に使用できるポリゴンを返す [`shapefile_coords_poly`](@ref) も参照してください。これは [`load`](@ref) のためのものです。
