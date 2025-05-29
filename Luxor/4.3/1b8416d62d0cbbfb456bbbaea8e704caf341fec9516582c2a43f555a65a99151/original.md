```
arrow(start::Point, finish::Point, height::Vector, action=:stroke;
    keyword arguments...)
```

Draw a Bézier arrow between `start` and `finish`, with control points defined to fit in an imaginary box defined by the two supplied `height` values (see `bezierfrompoints()`). If the height values are different signs, the arrow will change direction on its way.

Keyword arguments are the same as [`arrow(pt1, pt2, pt3, pt4)`](@ref).

### Example

```julia
arrow(pts[1], pts[end], [15, 15],
    decoration = 0.5,
    decorate = () -> text(string(pts[1])))
```
