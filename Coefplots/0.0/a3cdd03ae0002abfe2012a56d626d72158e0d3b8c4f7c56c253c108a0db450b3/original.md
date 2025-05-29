```
Mark
```

This enters `Coefplot.mark`, `Coefplot.errormark`, and that of `Multi-,` `Grouoped-`, `GroupedMultiCoefplot`.

# Constructors

```julia
Mark(;mark=missing, marksize=missing, linetype=missing, linewidth=missing, fill=missing, draw=missing)
```

# Keyword arguments

  * `mark::Union{Symbol, String, Missing}` is the shape of the mark.
  * `marksize::Union{Real, Missing}` is the size of the mark in pt.
  * `linetype::Union{Real, Missing}` is the type of line of the outline of the mark. Available choices are: `"solid"`, `"dotted"`, `"densely dotted"`, `"loosely dotted"`, `"dashed"`, `"densely dashed"`, `"loosely dashed"`, `"dash dot"`, `"densely dash dot"`, `"loosely dash dot"`, `"dash dot dot"`, `"densely dash dot dot"`, `"loosely dash dot dot"`.
  * `linewidth::Union{Real, Missing}` is the width of line of the outline of the mark.
  * `fill::Union{Color, Missing}` is the color used to fill the mark
  * `draw::Union{Color, Missing}` is the color used to draw the outline of the mark.
