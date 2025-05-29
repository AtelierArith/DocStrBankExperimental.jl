```
symband(x, y, Δy; bandscale=1.0, kwargs...)
symband(xy, Δy; bandscale=1.0, kwargs...)
```

点 `(x, y)` の周りに半径 `bandscale * Δy` の対称バンドをプロットします。

## 属性

`MakieCore.Plot{AbstractGPsMakie.symband}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  bandscale    1.0
  color        RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap     :viridis
  colorrange   MakieCore.Automatic()
  cycle        [:color => :patchcolor]
  inspectable  true
  linecolor    MakieCore.Automatic()
  linestyle    "nothing"
  linewidth    1.5
```
