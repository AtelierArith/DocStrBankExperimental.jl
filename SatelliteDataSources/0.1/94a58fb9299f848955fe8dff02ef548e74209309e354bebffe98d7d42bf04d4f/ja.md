```
RasterStack(x::AbstractSatellite, layers=bands(T); kwargs...)
```

複数のレイヤーを `Rasters.RasterStack` に読み込みます。

# パラメータ

  * `x`: レイヤーを読み込むための `AbstractSatellite`。
  * `layer`: 読み込むレイヤー。センサー `s` の利用可能なレイヤーのリストについては `layers(s)` を参照してください。
  * `kwargs`: サポートされているキーワードの概要については `Rasters.RasterStack` [ドキュメント](https://rafaqz.github.io/Rasters.jl/dev/reference/#Rasters.RasterStack) を参照してください。
