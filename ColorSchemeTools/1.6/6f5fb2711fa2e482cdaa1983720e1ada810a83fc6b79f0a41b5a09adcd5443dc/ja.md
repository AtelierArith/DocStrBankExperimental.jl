```
colorscheme_to_image(cs, nrows=50, tilewidth=5)
```

ColorSchemeから画像を作成します。`nrows`行にわたって色を繰り返し、各ピクセルを`tilewidth`回繰り返します。

画像を配列として返します。

例:

```
using FileIO

img = colorscheme_to_image(ColorSchemes.leonardo, 50, 200)
save("/tmp/cs_image.png", img)

save("/tmp/blackbody.png", colorscheme_to_image(ColorSchemes.blackbody, 10, 100))
```
