```
convert_to_scheme(cscheme, img)
```

Converts `img` from its current color values to use only the colors defined in the ColorScheme `cscheme`.

```
image = nonTransparentImg
convert_to_scheme(ColorSchemes.leonardo, image)
convert_to_scheme(ColorSchemes.Paired_12, image)
```
