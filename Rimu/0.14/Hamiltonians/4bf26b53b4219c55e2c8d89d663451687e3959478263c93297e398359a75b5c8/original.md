```
HardwallBoundaries(dims...) -> CubicGrid
HardwallBoundaries(dims) -> CubicGrid
```

Return a [`CubicGrid`](@ref) with all dimensions non-periodic. Equivalent to `CubicGrid(dims, (false, false, ...))`.
