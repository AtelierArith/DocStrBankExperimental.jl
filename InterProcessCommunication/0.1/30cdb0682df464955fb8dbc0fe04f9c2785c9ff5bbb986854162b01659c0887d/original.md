```
info = shminfo(arg)
```

yields information about the System V shared memory segment identified or associated with `arg`, the identifier of the shared memory segment, a shared array attached to the shared memory segment, or the System V IPC key associated with the shared memory segment.

See also [`ShmInfo`](@ref), [`ShmId`](@ref), [`shmget`](@ref), [`shmat`](@ref), and [`SharedMemory`](@ref).
