```
thread_position_in_grid_1d()::UInt32
thread_position_in_grid_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
thread_position_in_grid_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

Return the current thread's position in an N-dimensional grid of threads.
