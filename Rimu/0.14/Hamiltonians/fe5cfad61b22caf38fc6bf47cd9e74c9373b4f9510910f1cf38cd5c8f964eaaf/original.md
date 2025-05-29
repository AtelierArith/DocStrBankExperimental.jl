```
LadderBoundaries(dims...) -> CubicGrid
LadderBoundaries(dims) -> CubicGrid
```

Return a [`CubicGrid`](@ref) where the first dimension is dimensions non-periodic and the rest are periodic. Equivalent to `CubicGrid(dims, (true, false, ...))`.
