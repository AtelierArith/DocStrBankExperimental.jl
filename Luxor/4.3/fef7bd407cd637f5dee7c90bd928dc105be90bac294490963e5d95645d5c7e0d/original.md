```
 hexnearest_cubic(x::Real, y::Real, z::Real, origin, width, height)
```

Find the nearest hexagon in cubic coordinates, ie as `q`, `r`, `s` integer indices, given (x, y, z) as Real numbers, with the hexagonal grid centered at `origin`, and with tiles of `width`/`height`.

For more information about making hexagons and hexagonal grids, see [Luxor.Hexagon](@ref).
