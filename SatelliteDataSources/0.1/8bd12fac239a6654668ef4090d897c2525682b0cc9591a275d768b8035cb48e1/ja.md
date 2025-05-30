```
decode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRaster)
decode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRasterStack)
```

与えられたラスタのデジタル数（DN）値をデコードします。通常、デコードされた値は反射率（視覚バンド）またはケルビン（熱バンド）になります。

# パラメータ

  * `s`: 問題のラスタを生成した `AbstractSatellite`。
  * `raster`: デコードされる `Rasters.Raster` または `Rasters.RasterStack`。
