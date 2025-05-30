```
help_attributes([io], Union{PlotType, PlotFunction}; extended = false)
```

プロットタイプ `Typ` の属性のリストを返します。返される属性は `default_theme` に見られる属性を拡張したものです。

オプションのキーワード引数 `extended` (デフォルト = `false`) を使用して、各属性のデフォルト値も表示できます。使用例:

```example
>help_attributes(scatter)
    alpha
    color
    colormap
    colorrange
    distancefield
    glowcolor
    glowwidth
    linewidth
    marker
    marker_offset
    markersize
    overdraw
    rotations
    strokecolor
    strokewidth
    transform_marker
    transparency
    uv_offset_width
    visible
```
