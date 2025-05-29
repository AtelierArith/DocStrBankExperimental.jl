```
threadgroup_barrier(flag::MemoryFlags=MemoryFlagNone)
```

Synchronize all threads in a threadgroup.

Possible flags that affect the memory synchronization behavior are found in [`MemoryFlags`](@ref)
