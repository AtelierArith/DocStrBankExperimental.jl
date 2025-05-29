```
id = shmid(arg)
```

yields the identifier of an existing POSIX shared memory object or System V shared memory segment identifed by `arg` or associated with `arg`. Argument can be:

  * An instance of `SharedMemory`.
  * An instance of `WrappedArray` whose contents is stored into shared memory.
  * A string starting with a `'/'` (and no other `'/'`) to identify a POSIX shared memory object.
  * An instance of `IPC.Key` to specify a System V IPC key associated with a shared memory segment. In that case, an optional second argument `readonly` can be set `true` to only request read-only access; otherwise read-write access is requested.
  * An instance of `ShmId` to specify a System V shared memory segment.

See also: [`SharedMemory`](@ref), [`shmrm`](@ref).
