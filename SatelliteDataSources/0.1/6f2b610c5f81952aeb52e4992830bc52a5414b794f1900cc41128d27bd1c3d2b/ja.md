```
encode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRaster; encoding_type=UInt16, missingval=0x0000)
encode(s::Type{AbstractSatellite}, raster::Rasters.AbstractRasterStack; kwargs...)
```

提供されたラスタをデジタル数（DN）にエンコードします。

# パラメータ

  * `s`: 問題のラスタを生成した `AbstractSatellite`。
  * `raster`: エンコードされる `Rasters.Raster` または `Rasters.RasterStack`。
  * `encoding_type`: エンコードされた値を格納するために使用するJulia型（デフォルト = `UInt16`）。
  * `missingval`: 欠損値を示すための値（デフォルト = `0x0000`）。
