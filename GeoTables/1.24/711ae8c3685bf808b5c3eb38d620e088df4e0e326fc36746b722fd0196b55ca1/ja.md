```
georef(table, names; [crs], [lenunit])
```

`names` 列に保存されたポイントの座標を使用して `table` を地理参照します。

オプションで、デフォルトでヒューリスティックに基づいて設定される座標参照系 `crs` を指定できます。また、`lenunit`（単位なしの値の場合はデフォルトでメートル）を指定できますが、これはこの柔軟性を許可する CRS タイプでのみ使用できます。[CoordRefSystems.jl](https://github.com/JuliaEarth/CoordRefSystems.jl) からの任意の `CRS` または `EPSG`/`ESRI` コードがサポートされています。

## 例

```julia
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"))
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), crs=LatLon)
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), crs=EPSG{4326})
georef((a=rand(10), x=rand(10), y=rand(10)), ("x", "y"), lenunit=u"cm")
```
