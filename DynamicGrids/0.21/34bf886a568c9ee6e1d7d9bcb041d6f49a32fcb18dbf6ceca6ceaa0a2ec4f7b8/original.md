```
TextConfig

TextConfig(; kw...)
TextConfig(face, namepixels, namepos, timepixels, timepos, fcolor, bcolor)
```

Text configuration for printing timestep and grid name on the image.

# Arguments / Keywords

  * `font`: A `FreeTypeAbstraction.FTFont`, or a `String` with the font name to look for. The `FTFont` may load more quickly.
  * `namepixels` and `timepixels`: the pixel size of the font.
  * `timepos` and `namepos`: tuples that set the label positions, in `Int` pixels.
  * `fcolor` and `bcolor`: the foreground and background colors, as `ARGB32`.
