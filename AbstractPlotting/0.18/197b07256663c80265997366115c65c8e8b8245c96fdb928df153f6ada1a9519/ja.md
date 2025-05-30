```
band(x, ylower, yupper; kwargs...)
band(lower, upper; kwargs...)
```

`ylower`から`yupper`までのバンドを`x`に沿ってプロットします。`band(lower, upper)`の形式は、`lower`と`upper`の点の間に[ルールドサーフェス](https://en.wikipedia.org/wiki/Ruled_surface)をプロットします。

## 属性

`AbstractPlotting.Band`の利用可能な属性とそのデフォルトは次のとおりです：

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color => :patchcolor]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  interpolate     false
  lightposition   :eyeposition
  linewidth       1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
