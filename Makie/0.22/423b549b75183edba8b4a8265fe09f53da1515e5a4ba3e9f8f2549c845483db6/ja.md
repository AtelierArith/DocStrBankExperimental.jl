```
boundingbox(scenelike[, exclude = plot -> false])
```

`scenelike`の下に収集されたすべてのプロットの結合データ空間バウンディングボックスを返します。これには`plot.transformation`、すなわち`transform_func`と`model`行列が含まれます。`exclude(plot) == true`のプロットは除外されます。

参照: [`data_limits`](@ref)
