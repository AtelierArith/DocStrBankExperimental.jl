```
id = shmcfg(arg, perms) -> id
```

changes the access permissions of a System V IPC shared memory segment identified by `arg`, a System V IPC shared memory identifier, a shared array attached to a System V IPC shared memory segment, or a System V IPC key associated with a shared memory segment. Argument `perms` specifies bitwise flags with the new permissions. The identifier of the shared memory segment is returned.

See also [`ShmId`](@ref), [`shmget`](@ref), [`shmctl`](@ref) and [`SharedMemory`](@ref).
