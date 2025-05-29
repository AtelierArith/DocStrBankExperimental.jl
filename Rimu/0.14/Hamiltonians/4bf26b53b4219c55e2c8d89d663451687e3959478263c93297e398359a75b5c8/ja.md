```
HardwallBoundaries(dims...) -> CubicGrid
HardwallBoundaries(dims) -> CubicGrid
```

すべての次元が非周期的な [`CubicGrid`](@ref) を返します。これは `CubicGrid(dims, (false, false, ...))` と同等です。
