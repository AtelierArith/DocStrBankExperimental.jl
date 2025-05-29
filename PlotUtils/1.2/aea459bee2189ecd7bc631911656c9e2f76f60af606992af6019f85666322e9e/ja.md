```
cgrad(colors, [values]; categorical = nothing, scale = nothing, rev = false, alpha = nothing)
```

`colors` と `values` から Colorgradient を構築します。

`colors` は ColorSchemes.jl の `ColorScheme` のシンボル、`ColorScheme`、色のベクトル、`ColorGradient` または `ColorPalette` であることができます。`values` が整数の場合、指定された colorscheme から等間隔で選ばれる色の数を指定します。それ以外の場合はベクトルが受け入れられます。連続的な色のグラデーションでは、`values` は色が 0 と 1 の間でどこに位置するかを示します。カテゴリカルな色のグラデーションでは、`values` は色がどこで終わり、新しい色が 0 と 1 の間で始まるかを示します。0 と 1 は、すでに存在しない場合、`values` に追加されます。

`rev` が `true` の場合、色は反転します。`scale` はシンボル `:log`、`:log10`、`:log2`、`:ln`、`:exp`、`:exp10` または関数を受け入れます。`alpha` が設定されている場合、それはすべての色に適用されます。
