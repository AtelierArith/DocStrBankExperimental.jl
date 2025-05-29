```
arrows(points, directions; kwargs...)
arrows(x, y, u, v)
arrows(x::AbstractVector, y::AbstractVector, u::AbstractMatrix, v::AbstractMatrix)
arrows(x, y, z, u, v, w)
```

指定されたポイントに指定された成分で矢印をプロットします。`u` と `v` はベクトル成分として解釈され（`u` が x で `v` が y）、ベクトルは `x`、`y` で尾を持つようにプロットされます。

`x, y, u, v` が `<: AbstractVector` の場合、各「行」は単一のベクトルとしてプロットされます。

`u, v` が `<: AbstractMatrix` の場合、`x` と `y` はグリッドの仕様として解釈され、`u, v` はグリッドに沿って矢印としてプロットされます。

`arrows` は三次元でも動作します。

## 属性

`AbstractPlotting.Arrows` の利用可能な属性とそのデフォルトは次のとおりです：

```
  align           :origin
  ambient         Float32[0.55, 0.55, 0.55]
  arrowcolor      AbstractPlotting.Automatic()
  arrowhead       AbstractPlotting.Automatic()
  arrowsize       AbstractPlotting.Automatic()
  arrowtail       AbstractPlotting.Automatic()
  color           :black
  colormap        :viridis
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lengthscale     1.0f0
  lightposition   :eyeposition
  linecolor       AbstractPlotting.Automatic()
  linestyle       "nothing"
  linewidth       AbstractPlotting.Automatic()
  markerspace     AbstractPlotting.Pixel
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  normalize       false
  overdraw        false
  quality         32
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
