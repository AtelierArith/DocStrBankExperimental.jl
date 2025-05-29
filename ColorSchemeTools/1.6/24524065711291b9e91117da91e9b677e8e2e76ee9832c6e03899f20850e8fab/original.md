```
colorscheme_weighted(colorscheme, weights, length)
```

Returns a new ColorScheme of length `length` (default 50) where the proportion of each color in `colorscheme` is represented by the associated weight of each entry.

Examples:

```
colorscheme_weighted(extract_weighted_colors("hokusai.jpg")...)
colorscheme_weighted(extract_weighted_colors("filename00000001.jpg")..., 500)
```
