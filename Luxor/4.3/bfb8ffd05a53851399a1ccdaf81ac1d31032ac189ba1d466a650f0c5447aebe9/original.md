```
getpath()
```

Get the current path and return a CairoPath object, which is an array of `element_type` and `points` objects. With the results you can step through and examine each entry like this:

```julia
o = getpath()
x, y = currentpoint()
for e in o
    if e.element_type == Cairo.CAIRO_PATH_MOVE_TO
        (x, y) = e.points
        move(x, y)
    elseif e.element_type == Cairo.CAIRO_PATH_LINE_TO
        (x, y) = e.points
        # straight lines
        line(x, y)
        strokepath()
        circle(x, y, 1, :stroke)
    elseif e.element_type == Cairo.CAIRO_PATH_CURVE_TO
        (x1, y1, x2, y2, x3, y3) = e.points
        # Bezier control lines
        circle(x1, y1, 1, :stroke)
        circle(x2, y2, 1, :stroke)
        circle(x3, y3, 1, :stroke)
        move(x, y)
        curve(x1, y1, x2, y2, x3, y3)
        strokepath()
        (x, y) = (x3, y3) # update current point
    elseif e.element_type == Cairo.CAIRO_PATH_CLOSE_PATH
        closepath()
    else
        error("unknown CairoPathEntry " * repr(e.element_type))
        error("unknown CairoPathEntry " * repr(e.points))
    end
end
```
