```
shmrm(arg)
```

removes the shared memory associated with `arg`. If `arg` is a name, the corresponding POSIX named shared memory is unlinked. If `arg` is a key or identifier of a BSD shared memory segment, the segment is marked to be eventually destroyed. Argument `arg` can also be a `SharedMemory` object.

The `rm` method may also be called to remove an existing shared memory segment or object. There are several possibilities:

```julia
rm(SharedMemory, name)  # `name` identifies a POSIX shared memory object
rm(SharedMemory, key)   # `key` is associated with a BSD shared memory segment
rm(id)                  # `id` is the identifier of a BSD shared memory segment
rm(shm)                 # `shm` is an instance of `SharedMemory`
```

See also: [`SharedMemory`](@ref), [`shmid`](@ref), [`shmat`](@ref).
