```
barplot(x, y; kwargs...)
```

棒グラフをプロットします。`y`は高さを定義します。`x`と`y`は1次元である必要があります。

## 属性

`AbstractPlotting.BarPlot`の利用可能な属性とそのデフォルトは次のとおりです：

```
  color        RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap     :viridis
  colorrange   AbstractPlotting.Automatic()
  cycle        [:color => :patchcolor]
  direction    :y
  dodge        AbstractPlotting.Automatic()
  dodge_gap    0.03
  fillto       AbstractPlotting.Automatic()
  inspectable  true
  marker       GeometryBasics.HyperRectangle
  n_dodge      AbstractPlotting.Automatic()
  stack        AbstractPlotting.Automatic()
  strokecolor  :black
  strokewidth  0
  visible      true
  width        AbstractPlotting.Automatic()
  x_gap        0.2
```
