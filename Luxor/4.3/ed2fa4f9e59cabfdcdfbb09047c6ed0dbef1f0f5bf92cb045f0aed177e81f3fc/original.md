```
boxmap(A::Array, pt, w, h)
```

Build a box map of the values in `A` with one corner at `pt` and width `w` and height `h`. There are `length(A)` boxes. The areas of the boxes are proportional to the original values, scaled as necessary.

The return value is an array of BoxmapTiles. For example:

```julia
[BoxmapTile(0.0, 0.0, 10.0, 20.0)
 BoxmapTile(10.0, 0.0, 10.0, 13.3333)
 BoxmapTile(10.0, 13.3333, 10.0, 6.66667)]
```

with each tile containing `(x, y, w, h)`. `box()` and `BoundingBox()` can work with BoxmapTiles as well.

# Example

```julia
using Luxor
@svg begin
    fontsize(16)
    fontface("HelveticaBold")
    pt = Point(-200, -200)
    a = rand(10:200, 15)
    tiles = boxmap(a, Point(-200, -200), 400, 400)
    for (n, t) in enumerate(tiles)
        randomhue()
        bb = BoundingBox(t)
        box(bb - 2, :stroke)
        box(bb - 5, :fill)
        sethue("white")
        text(string(n), midpoint(bb[1], bb[2]), halign=:center)
    end
end 400 400 "boxmap.svg"
```
