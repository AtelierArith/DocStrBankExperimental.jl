```
threadgroups_per_grid_1d()::UInt32
threadgroups_per_grid_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
threadgroups_per_grid_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

グリッドあたりのスレッドグループの数を返します。
