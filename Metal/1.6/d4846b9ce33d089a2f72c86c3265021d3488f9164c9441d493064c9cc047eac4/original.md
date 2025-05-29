```
grid_origin_1d()::UInt32
grid_origin_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
grid_origin_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

Return the origin offset of the grid for threads that read per-thread stage-in data.
