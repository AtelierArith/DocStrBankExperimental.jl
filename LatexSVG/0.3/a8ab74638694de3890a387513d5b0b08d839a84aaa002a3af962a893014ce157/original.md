```
savesvg(filepath::AbstractString, svg::LaTeXSVG; web_display=false, web_inline=false)
```

Saves `svg` to `filepath`.

If `web_display=true`, some adjustments are made to the SVG before it is saved:

  * The height of the SVG is scaled by a factor of 1.2 and its unit changed to `rem`, and the width attribute is deleted.
  * A style attribute `style="display: block; margin: auto; max-width: 80%"` is added.
  * A `class="latexsvg-display"` attribute is added to the `<svg>` tag.

If `web_inline=true`, the following adjustments are made:

  * The height of the SVG is scaled by a factor of 1.2 and its unit changed to `rem`, and the width attribute is deleted.
  * A style attribute `style="vertical-align: middle"` is added.
  * A `class="latexsvg-inline"` attribute is added.

Refer to the documentation for details.

Note that `web_display` and `web_inline` cannot both be `true`. If they are both `false`, the vanilla SVG output is saved with no modification.
