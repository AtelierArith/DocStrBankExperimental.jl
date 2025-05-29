```
sortcolorscheme(colorscheme::ColorScheme, field; kwargs...)
```

LUVカラースペースのフィールドを使用して、カラースキームを（非破壊的に）ソートします。

小なり関数は `lt = (x,y) -> compare_colors(x, y, field)` です。

デフォルトは輝度フィールド `:l` でソートしますが、`:u` または `:v` でソートすることもできます。

新しいColorSchemeを返します。
