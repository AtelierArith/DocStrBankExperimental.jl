```
BezierPath(svg::AbstractString; fit = false, bbox = nothing, flipy = false, flipx = false, keep_aspect = true)
```

Construct a `BezierPath` using a string of [SVG path commands](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d#path_commands). The commands will be parsed first into `MoveTo`, `LineTo`, `CurveTo`, `EllipticalArc` and `ClosePath` objects which are then passed to the `BezierPath` constructor.

If `fit === true`, the path will be scaled to fit into a square of width 1 centered on the origin. If, additionally, `bbox` is set to some `Rect`, the path will be fit into this rectangle instead. If you want to use a path as a scatter marker, it is usually good to fit it so that it's centered and of a comparable size relative to other scatter markers.

If `flipy === true` or `flipx === true`, the respective dimensions of the path will be flipped. Makie uses a coordinate system where y=0 is at the bottom and y increases upwards while in SVG, y=0 is at the top and y increases downwards, so for most SVG paths `flipy = true` will be needed.

If `keep_aspect === true`, the path will be fit into the bounding box such that its longer dimension fits and the other one is scaled to retain the original aspect ratio. If you set `keep_aspect = false`, the new boundingbox of the path will be the one it is fit to, but note that this can result in a squished appearance.

## Example

Construct a triangular `BezierPath` out of a path command string and use it as a scatter marker:

```julia
str = "M 0,0 L 10,0 L 5,10 z"
bp = BezierPath(str, fit = true)
scatter(1:10, marker = bp, markersize = 20)
```
