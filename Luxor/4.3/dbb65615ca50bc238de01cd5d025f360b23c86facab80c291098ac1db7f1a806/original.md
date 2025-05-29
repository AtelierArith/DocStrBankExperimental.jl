```
hexagons_within(n::Int, hex::Hexagon)
```

Return all the hexagons within index distance `n` of `hex`. If `n` is 0, only the `hex` itself is returned. If `n` is 1, `hex` and the six hexagons one index away are returned. If `n` is 2, 19 hexagons surrounding `hex` are returned.

For more information about making hexagons and hexagonal grids, see [Luxor.Hexagon](@ref).
