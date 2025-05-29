```
Legend
```

This enters `MultiCoefplot.legend`. It determines the style of the legend. The content of the legend is defined by the title of the `Coefplot`.

# Constructors

```julia
Legend(;anchor=missing, at=missing, font=missing, size=missing)
```

# Keyword arguments

  * `anchor::Union{Symbol, String, Missing}` specifies the anchor of the legend box that is used for alignment. A typical one would be `"north west"`.
  * `at::Any` specifies the location in the axis frame that the anchor should adhere to. A typical one would be `(1, 0)`, which means that the anchor is fixed to the south-east corner of the axis frame.
  * `font::Union{Symbol, String, Missing}` is the font in which the legend should be printed in.
  * `size::Union{Real, Missing}` is the font size.
