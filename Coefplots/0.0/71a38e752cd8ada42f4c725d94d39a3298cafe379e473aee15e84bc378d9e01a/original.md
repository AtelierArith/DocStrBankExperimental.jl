```
CaptionStyle
```

This enters `Coefplot.xticklabel`, `Coefplot.yticklabel`,  `Coefplot.xlabel.captionstyle`, `Coefplot.ylabel.captionstyle`,  `Coefplot.title.captionstyle`, `Coefplot.note.captionstyle`.

# Constructors

```julia
CaptionStyle(;font=missing, size=missing, rotate=missing)
```

# Keyword arguments

  * `font::Union{Symbol, String, Missing}` contains the font's T1 code
  * `size::Union{Real, Missing}` is the font's size in pt.
  * `rotate::Union{Real, Missing}` is the rotation angle counterclockwise for the caption.
