```
threadgroup_position_in_grid_1d()::UInt32
threadgroup_position_in_grid_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
threadgroup_position_in_grid_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

現在のスレッドグループのグリッド内でのユニークな位置を返します。
