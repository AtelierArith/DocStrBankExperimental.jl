```
dispatch_threads_per_threadgroup_1d()::UInt32
dispatch_threads_per_threadgroup_2d()::NamedTuple{(:x, :y), Tuple{UInt32, UInt32}}
dispatch_threads_per_threadgroup_3d()::NamedTuple{(:x, :y, :z), Tuple{UInt32, UInt32, UInt32}}
```

Return the thread execution width specified at dispatch for a threadgroup.
