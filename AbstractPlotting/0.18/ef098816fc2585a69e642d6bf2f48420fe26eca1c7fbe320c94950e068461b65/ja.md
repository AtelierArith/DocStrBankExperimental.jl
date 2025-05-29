```
rangebars(val, low, high; kwargs...)
rangebars(val, low_high; kwargs...)
rangebars(val_low_high; kwargs...)
```

`val`で1次元の範囲バーをプロットし、選択した`direction`に応じて他の次元で`low`から`high`まで延長します。

参照値に対するエラーをプロットしたい場合は、`errorbars`を使用してください。

## 属性

`AbstractPlotting.Rangebars`の利用可能な属性とそのデフォルトは次のとおりです：

```
  color         :black
  colormap      :viridis
  direction     :y
  inspectable   true
  linewidth     1.5
  visible       true
  whiskerwidth  0
```
