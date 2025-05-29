```
colorscheme_to_image(cs, nrows=50, tilewidth=5)
```

Make an image from a ColorScheme by repeating the colors in `nrows` rows, repeating each pixel `tilewidth` times.

Returns the image as an array.

Examples:

```
using FileIO

img = colorscheme_to_image(ColorSchemes.leonardo, 50, 200)
save("/tmp/cs_image.png", img)

save("/tmp/blackbody.png", colorscheme_to_image(ColorSchemes.blackbody, 10, 100))
```
