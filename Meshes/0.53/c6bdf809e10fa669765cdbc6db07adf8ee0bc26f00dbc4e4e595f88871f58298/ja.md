```
Proj(CRS)
Proj(code)
```

幾何学または領域の座標を指定された座標参照系 `CRS` または EPSG/ESRI `code` に変換します。

オプションとして、この変換は多面体の `boundary` をサンプリングし、もしこのオプションが `true` であれば、マニフォールド変換で発生する歪みを処理します。

## 例

```julia
Proj(Polar)
Proj(WebMercator)
Proj(Mercator{WGS84Latest})
Proj(EPSG{3395})
Proj(ESRI{54017})
```

### 注意事項

デフォルトでは、多面体の頂点のみが変換され、マニフォールド変換で発生する歪みは無視されます。この場合を処理するには、[`TransformedGeometry`](@ref) を使用してください。
