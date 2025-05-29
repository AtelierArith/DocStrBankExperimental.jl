`BoundingBox()` with no arguments returns a BoundingBox that includes the current drawing.

The default `BoundingBox(;centered=true)` returns a BoundingBox the same size and position as the current drawing, and assumes the origin (0, 0) is at the center.

If the `centered` option is `false`, the function assumes that the origin is at the top left of the drawing. So this function doesn't really work if the current matrix has been modified (by `translate()`, `scale()`, `rotate()` etc.)

An instance of the BoundingBox type holds two Points, `corner1` and `corner2`.

```julia
BoundingBox(;centered = true)   # the bounding box of the Drawing
```

```julia
BoundingBox(s::AbstractString)  # the bounding box of a text string at the origin
```

```julia
BoundingBox(pt::Array)          # the bounding box of a polygon
```

```julia
BoundingBox(circle(O, 100))     # the bounding box of a path added by circle()
```

```julia
BoundingBox(path::Path)         # the bounding box of a Path
```

You can use `BoundingBox()` with the functions that add graphic shapes to the current path (eg `box()`, `circle()`, `star()`, `ngon()`). But note that eg `BoundingBox(box(O, 100, 100))` adds a shape to the current path as well as returning a bounding box.
