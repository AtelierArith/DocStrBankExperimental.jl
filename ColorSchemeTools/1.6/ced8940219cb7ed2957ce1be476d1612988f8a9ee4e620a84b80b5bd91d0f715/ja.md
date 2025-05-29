```
convert_to_scheme(cscheme, img)
```

`img`を現在の色値からColorScheme `cscheme`で定義された色のみを使用するように変換します。

```
image = nonTransparentImg
convert_to_scheme(ColorSchemes.leonardo, image)
convert_to_scheme(ColorSchemes.Paired_12, image)
```
