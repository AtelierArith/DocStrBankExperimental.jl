```
LaTeXSVG(latex::AbstractString, svg::String; standalone::Bool=false)
```

This type contains the LaTeX code to be rendered, the preamble, and the rendered SVG string. Both [`latexsvg`](@ref) and [`@Lsvg_str`](@ref) return objects of this type.

`LaTeXSVG` objects contain 4 fields:

  * `latex` contains the LaTeX input.
  * `standalone` indicates whether `latex` is a complete LaTeX document. If `standalone=true` then `pre` is empty.
  * `pre` is a vector of strings containing the preamble, which is recorded from the global preamble when a `LaTeXSVG` object is contructed, namely when `latexsvg` or `@Lsvg_str` is called.
  * `svg` contains the SVG string.

You can access these fields with the usual dot syntax.

!!! note
    You should never need to contruct a `LaTeXSVG` object yourself.


!!! note
    If you are using VSCode, by default the color of the SVG displayed in the plot pane adapts to the color scheme of VSCode (black for light mode and white for dark mode.) Rest assured that this adaptive color is not written into the SVG itself. Also, if you defined custom colors in your LaTeX, it should be displayed (and saved to file) faithfully.

