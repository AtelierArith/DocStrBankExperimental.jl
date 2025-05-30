```
Raster(x::AbstractSatellite, layer::Symbol; kwargs...)
```

単一のレイヤーを `Rasters.Raster` に読み込みます。

# パラメータ

  * `x`: レイヤーを読み込むための `AbstractSatellite`。
  * `layer`: 読み込むレイヤー。センサー `s` の利用可能なレイヤーのリストについては `layers(s)` を参照してください。
  * `kwargs`: サポートされているキーワードの概要については `Rasters.Raster` [ドキュメント](https://rafaqz.github.io/Rasters.jl/dev/reference/#Rasters.Raster) を参照してください。
