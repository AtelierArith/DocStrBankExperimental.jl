```
georef(table, coords; [crs], [lenunit])
```

座標 `coords` を持つ点の `table` を地理参照します。

オプションで、デフォルトでヒューリスティックに基づいて設定される座標参照系 `crs` を指定し、`lenunit`（単位なしの値の場合はデフォルトでメートル）を指定できます。これは、この柔軟性を許可する CRS タイプでのみ使用できます。[CoordRefSystems.jl](https://github.com/JuliaEarth/CoordRefSystems.jl) からの任意の `CRS` または `EPSG`/`ESRI` コードがサポートされています。

## 例

```julia
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)])
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], crs=LatLon)
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], crs=EPSG{4326})
julia> georef((a=[1, 2, 3], b=[4, 5, 6], [(0, 0), (1, 1), (2, 2)], lenunit=u"cm")
```
