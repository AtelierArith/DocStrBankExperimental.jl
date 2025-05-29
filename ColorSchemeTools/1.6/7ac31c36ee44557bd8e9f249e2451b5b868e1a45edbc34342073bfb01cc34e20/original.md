```
compare_colors(color_a, color_b, field = :l)
```

Compare two colors, using the Luv colorspace. `field` defaults to luminance `:l` but could be `:u` or `:v`. Return true if the specified field of `color_a` is less than `color_b`.
