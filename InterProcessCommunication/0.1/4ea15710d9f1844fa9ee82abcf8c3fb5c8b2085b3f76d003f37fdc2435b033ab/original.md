```
shmdt(ptr)
```

detaches a System V shared memory segment from the address space of the caller. Argument `ptr` is the pointer returned by a previous [`shmat`](@ref) call.

See also: [`shmat`](@ref), [`shmget`](@ref).
