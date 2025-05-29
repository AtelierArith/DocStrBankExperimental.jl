```
axislegend(ax, args...; position = :rt, kwargs...)
axislegend(ax, args...; position = (1, 1), kwargs...)
axislegend(ax = current_axis(); kwargs...)
axislegend(title::String; kwargs...)
```

Axisのプロット領域内に配置される凡例を作成します。

位置はシンボルで、最初の文字が水平方向の配置を制御し、l、r、またはcを指定できます。2番目の文字は垂直方向の配置を制御し、t、b、またはcを指定できます。また、タプルとして指定することもでき、最初の要素が凡例の水平方向の配置（halign）、2番目の要素が垂直方向の配置（valign）として設定されます。
