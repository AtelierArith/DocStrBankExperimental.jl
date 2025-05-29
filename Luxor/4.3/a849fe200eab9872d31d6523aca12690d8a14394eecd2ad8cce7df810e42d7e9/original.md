```
polycross(pt::Point, radius, npoints::Int, ratio=0.5, orientation=0.0;
    action      = :none,
    splay       = 0.5,
    vertices    = false,
    reversepath = false)
polycross(pt::Point, radius, npoints::Int, ratio=0.5, orientation=0.0, action;
    splay       = 0.5,
    vertices    = false,
    reversepath = false)
```

Make a cross-shaped polygon with `npoints` arms to fit inside a circle of radius `radius` centered at `pt`.

`ratio` specifies the ratio of the two sides of each arm. `splay` makes the arms ... splayed.

Use `vertices=true` to return the vertices of the shape instead of executing the action.

(Adapted from Compose.jl.xgon()))

## Examples

```julia
polycross(O, 100, 5,
    action = :fill,
    splay  = 0.5)
```

```julia
polycross(O, 120, 5, 0.5, 0.0, :stroke,
    splay  = 0.5)
```
