```
html_fixed_size(mol::SimpleMolGraph, width, height) -> HTML{String}
```

SVG要素の固定サイズHTMLラッパーを生成します。

widthおよびheight引数は、数値（`px`に変換されます）または`100%`のようなCSS文字列であることができます。
