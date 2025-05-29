```
Path2D(points;label="",pen=Pen(),arrow=NoArrow(),spline=false)
Path2D(x,y;label="",pen=Pen(),arrow=NoArrow(),spline=false)
```

A graphics primitive representing a two-dimensional path

`points` may be an Array of `Vec2`s, an Array of 2-tuples, or an $n × 2$ Array. Alternatively, iterables of coordinates may be supplied separately as `x` and `y`

# Examples

```julia-repl
julia> Path2D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
Path2D(<3 points>;pen=MidnightBlue)
```
