```
DotMatrix(; pixelsize, pixelspacing=pixelsize,
            rounding=zero(pixelsize), meta::Meta=GDSMeta(0,0))
```

# Keyword args

  * `pixelsize`: dimension for the width/height of each pixel.
  * `pixelspacing`: dimension for the spacing between adjacent pixels. Should be ≥ pixelsize. Defaults to `pixelsize`.
  * `rounding`: rounding radius for sharp corners of pixels. If `pixelsize == pixelspacing`, individual pixels are not rounded, but rather the pixels are unioned and the entire letter will be rounded.
  * `meta`: layer/datatype or similar info.
