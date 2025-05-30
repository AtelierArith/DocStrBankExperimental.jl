```
savi(src::AbstractSatellite; L=0.33)
savi(::Type{AbstractSatellite}, stack::AbstractRasterStack; L=0.33)
savi(nir::AbstractRaster, red::AbstractRaster; L=0.33, scale=1.0, offset=0.0)
```

土壌調整植生指数（Huete 1988）を計算します。

SAVIは、土壌の明るさの影響を最小限に抑えることを試みる植生指数で、土壌の明るさ補正係数（L）を導入します。

SAVI = ((nir - red) / (nir + red + L)) * (1 + L)

# キーワード

  * `L`: 植生被覆の量で、1.0は植生がないことを意味し、0.0は高い植生を意味します。
  * `scale`: デジタル数値を反射率に変換するためのスケーリング係数。
  * `offset`: デジタル数値を反射率に変換するためのオフセット。
