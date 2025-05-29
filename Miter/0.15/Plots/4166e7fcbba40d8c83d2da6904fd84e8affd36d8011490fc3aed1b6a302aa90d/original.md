```julia
Circles(
    x_y_w,
    scale;
    stroke_color,
    stroke_width,
    fill_color
)

```

Taking an iterator or vector of `(x, y, w)` triplets (eg `NTuple{3}`, but anything iterable with 3 elements will do), draw circles centered on `(x, y)` coordinates with radius `scale * √w`.

# Keyword arguments

`stroke_color` determines the stroke color, using `nothing` if circles should not be stroked. `stroke_width` determines the stroke with if applicable.

`fill_color` determines the fill color of circles.
