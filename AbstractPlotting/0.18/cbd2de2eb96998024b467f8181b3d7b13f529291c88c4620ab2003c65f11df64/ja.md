```
scatter(positions)
scatter(x, y)
scatter(x, y, z)
```

`(x, y, z)`、`(x, y)`、または `positions` の各要素に対してマーカーをプロットします。

## 属性

`AbstractPlotting.Scatter` の利用可能な属性とそのデフォルトは次のとおりです：

```
  ambient           Float32[0.55, 0.55, 0.55]
  color             :black
  colormap          :viridis
  colorrange        AbstractPlotting.Automatic()
  cycle             [:color]
  diffuse           Float32[0.4, 0.4, 0.4]
  distancefield     "nothing"
  glowcolor         RGBA{N0f8}(0.0,0.0,0.0,0.0)
  glowwidth         0.0
  inspectable       true
  lightposition     :eyeposition
  linewidth         1
  marker            GeometryBasics.Circle
  marker_offset     AbstractPlotting.Automatic()
  markersize        9
  markerspace       AbstractPlotting.Pixel
  nan_color         RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw          false
  rotations         AbstractPlotting.Billboard{Float32}(0.0f0)
  shininess         32.0f0
  specular          Float32[0.2, 0.2, 0.2]
  ssao              false
  strokecolor       :black
  strokewidth       0
  transform_marker  false
  transparency      false
  uv_offset_width   Float32[0.0, 0.0, 0.0, 0.0]
  visible           true
```
