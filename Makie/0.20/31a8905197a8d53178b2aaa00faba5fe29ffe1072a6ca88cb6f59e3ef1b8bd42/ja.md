```
band(x, ylower, yupper; kwargs...)
band(lower, upper; kwargs...)
```

`ylower`から`yupper`までのバンドを`x`に沿ってプロットします。`band(lower, upper)`の形式は、`lower`と`upper`の点の間に[ルールドサーフェス](https://en.wikipedia.org/wiki/Ruled_surface)をプロットします。

## 属性

`MakieCore.Plot{Makie.band}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  alpha           1.0
  backlight       0.0f0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color => :patchcolor]
  depth_shift     0.0f0
  diffuse         1.0
  highclip        MakieCore.Automatic()
  inspectable     true
  interpolate     true
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  shading         MakieCore.NoShading
  shininess       32.0f0
  space           :data
  specular        0.2
  ssao            false
  transparency    false
  visible         true
```
