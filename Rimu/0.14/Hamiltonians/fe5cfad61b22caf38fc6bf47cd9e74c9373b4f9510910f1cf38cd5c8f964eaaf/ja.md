```
LadderBoundaries(dims...) -> CubicGrid
LadderBoundaries(dims) -> CubicGrid
```

最初の次元が非周期的で、残りが周期的な [`CubicGrid`](@ref) を返します。これは `CubicGrid(dims, (true, false, ...))` と同等です。
