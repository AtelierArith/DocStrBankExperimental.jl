```
Polygon2D(points;pen=Pen(),
                 fillpen=Pen(color="white"),
                 spline=false)
```

A graphics primitive representing a two-dimensional polygon

`points` may be an Array of `Vec2`s, an Array of 2-tuples, or an $n × 2$ Array. Alternatively, iterables of coordinates may be supplied separately as `x` and `y`

# Examples

```julia-repl
julia> Polygon2D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
Polygon2D(<3 points>;pen=MidnightBlue)
```
