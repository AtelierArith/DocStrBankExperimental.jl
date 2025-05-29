```
blendadjust(ablend, center::Point, xscale, yscale, rot=0)
```

Modify an existing blend by scaling, translating, and rotating it so that it will fill a shape properly even if the position of the shape is nowhere near the original location of the blend's definition.

For example, if your blend definition was this (notice the `1`)

```julia
blendgoldmagenta = blend(
    Point(0, 0), 0,                   # first circle center and radius
    Point(0, 0), 1,                   # second circle center and radius
    "gold",
    "magenta"
)
```

you can use it in a shape that's 100 units across and centered at `pos`, by calling this:

```
blendadjust(blendgoldmagenta, Point(pos.x, pos.y), 100, 100)
```

then use `setblend()`:

```
setblend(blendgoldmagenta)
```
