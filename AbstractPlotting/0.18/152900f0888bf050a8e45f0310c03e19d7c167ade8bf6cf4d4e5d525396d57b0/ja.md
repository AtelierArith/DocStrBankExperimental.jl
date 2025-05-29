```
errorbars(x, y, error_both; kwargs...)
errorbars(x, y, error_low, error_high; kwargs...)
errorbars(x, y, error_low_high; kwargs...)

errorbars(xy, error_both; kwargs...)
errorbars(xy, error_low, error_high; kwargs...)
errorbars(xy, error_low_high; kwargs...)

errorbars(xy_error_both; kwargs...)
errorbars(xy_error_low_high; kwargs...)
```

xy位置にエラーバーをプロットし、指定された`direction`のエラーによって拡張します。

相対エラーの代わりに低値から高値までの区間をプロットしたい場合は、`rangebars`を使用してください。

## 属性

`AbstractPlotting.Combined{AbstractPlotting.errorbars!}`の利用可能な属性とそのデフォルトは次のとおりです: 

```

```
