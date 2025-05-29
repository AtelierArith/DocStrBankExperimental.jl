```
Point2D(x::Real,y::Real; label="",pen=Pen())
Point2D(P; label="",pen=Pen())
```

A graphics primitive representing a two-dimensional point.

`P` may be a 2-tuple of real numbers, a `Vec2`, or a `Complex`

# Examples

```julia-repl
julia> Point2D(3,-1;pen="DarkGreen")
Point2D(3,-1;pen=DarkGreen)
```
