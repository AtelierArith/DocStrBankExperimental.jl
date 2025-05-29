```
Pattern(image)
Pattern(mask[; color1, color2])
```

Creates an `ImagePattern` from an `image` (a matrix of colors) or a `mask` (a matrix of real numbers). The pattern can be passed as a `color` to a plot to texture it. If a `mask` is passed, one can specify to colors between which colors are interpolated.
