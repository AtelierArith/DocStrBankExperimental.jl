```
Colorfier(values; [alphas, colorscheme, colorrange])
```

`values`内の各値を色にマッピングします。色は[`Colorfy.colors`](@ref)関数を使用して取得できます。

## オプション

  * `alphas` - スカラーまたは色のアルファのベクトル（デフォルトは`Colorfy.defaultalphas(values)`）;
  * `colorscheme` - スキーム名または`ColorSchemes.ColorScheme`オブジェクト（デフォルトは`Colorfy.defaultcolorscheme(values)`）;
  * `colorrange` - 最小および最大の色値を持つタプル、または`ColorSchemes.get`関数の`rangescale`引数に渡すことができるシンボル（デフォルトは`Colorfy.defaultcolorrange(values)`）;
