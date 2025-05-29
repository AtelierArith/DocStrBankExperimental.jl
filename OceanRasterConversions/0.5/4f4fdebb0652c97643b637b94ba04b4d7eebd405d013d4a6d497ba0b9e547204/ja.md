```
function depth_to_pressure(raster::Raster)
function depth_to_pressure(stack::RasterStack)
```

深さ次元（`Z`）を `GibbsSeaWater.jl` の `gsw_p_from_z` を使用して圧力に変換します。圧力は深さと*緯度*に依存するため、返される圧力は垂直深さ次元を置き換えるのではなく、結果の `Raster` 内の変数として保存されます。
