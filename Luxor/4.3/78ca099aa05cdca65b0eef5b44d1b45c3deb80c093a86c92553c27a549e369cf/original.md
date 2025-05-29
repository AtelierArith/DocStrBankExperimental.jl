```
blend(centerpos1, rad1, centerpos2, rad2, color1, color2)
```

Create a radial blend.

Example:

```julia
redblue = blend(
    pos, 0,                   # first circle center and radius
    pos, tiles.tilewidth/2,   # second circle center and radius
    "red",
    "blue",
)
```
