```
thread_position_in_threadgroup_1d()::UInt32
thread_position_in_threadgroup_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
thread_position_in_threadgroup_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

Return the current thread's unique position within a threadgroup.
