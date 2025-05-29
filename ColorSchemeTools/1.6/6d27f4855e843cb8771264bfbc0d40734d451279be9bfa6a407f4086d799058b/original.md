```
sortcolorscheme(colorscheme::ColorScheme, field; kwargs...)
```

Sort (non-destructively) a colorscheme using a field of the LUV colorspace.

The less than function is `lt = (x,y) -> compare_colors(x, y, field)`.

The default is to sort by the luminance field `:l` but could be by `:u` or `:v`.

Returns a new ColorScheme.
