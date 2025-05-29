```
BezierPath(commands::Vector)
```

Construct a `BezierPath` with a vector of path commands. The available path commands are

  * `MoveTo`
  * `LineTo`
  * `CurveTo`
  * `EllipticalArc`
  * `ClosePath`

A `BezierPath` can be used in certain places in Makie as an alternative to a polygon or a collection of lines, for example as an input to `poly` or `lines`, or as a `marker` for `scatter`.

The benefit of using a `BezierPath` is that curves do not need to be converted into a vector of vertices by the user. CairoMakie can use the path commands directly when it writes vector graphics which is more efficient and uses less space than approximating them visually using line segments.
