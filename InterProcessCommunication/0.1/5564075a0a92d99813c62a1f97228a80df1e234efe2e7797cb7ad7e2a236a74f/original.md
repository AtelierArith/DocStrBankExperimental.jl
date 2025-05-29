```
ptr = shmat(id, readonly)
```

attaches a System V shared memory segment to the address space of the caller. Argument `id` is the identifier of the shared memory segment. Boolean argument `readonly` specifies whether to attach the segment for read-only access; otherwise, the segment is attached for read and write accesses and the process must have read and write permissions for the segment. The returned value is the address of the shared memory segment for the caller.

See also: [`shmdt`](@ref), [`shmrm`](@ref).
