```
device_synchronize()
```

Block for all the operations on the device to complete. This is a heavyweight operation, typically you only need to call [`synchronize()`](@ref) which only synchronizes the stream associated with the current task.

On the device, `device_synchronize` acts as a synchronization point for child grids in the context of dynamic parallelism.
