A Path object contains, in the `.path` field, a vector of `PathElement`s (`PathCurve`, `PathMove`, `PathLine`, `PathClose`) that describe a Cairo path. Use `drawpath()` to draw it.

```julia
Path([PathMove(Point(2.0, 90.5625)),
      PathCurve(Point(4.08203, 68.16015), Point(11.28, 45.28), Point(24.8828, 26.40234)),
      PathLine(Point(2.0, 90.5625)),
      PathClose()
     ])
```
