```
getworldposition(pt::Point = O;
    centered=true)
```

Return the world coordinates of `pt`.

The default coordinate system for Luxor drawings is that the top left corner is 0/0. If you use `origin()` (or the various `@-` macro shortcuts), everything moves to the center of the drawing, and this function with the default `centered` option assumes an `origin()` function. If you choose `centered=false`, the returned coordinates will be relative to the top left corner of the drawing.

```julia
origin()
translate(120, 120)
@show currentpoint()      # => Point(0.0, 0.0)
@show getworldposition()  # => Point(120.0, 120.0)
```
