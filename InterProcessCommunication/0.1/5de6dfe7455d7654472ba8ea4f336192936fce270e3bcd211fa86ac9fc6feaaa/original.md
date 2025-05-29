```
shm = SharedMemory(id, len; perms=0o600, volatile=true)
```

creates a new shared memory object identified by `id` and whose size is `len` bytes. The identifier `id` can be a string starting by a `'/'` to create a POSIX shared memory object or a System V IPC key to create a System V shared memory segment. In this latter case, the key can be `IPC.PRIVATE` to automatically create a non-existing shared memory segment.

Keyword `perms` is to specify the access permissions to be granted. By default, only reading and writing by the user are granted.

Keyword `volatile` is to specify whether the shared memory is volatile or not. If non-volatile, the shared memory will remain accessible until explicit destruction or system reboot. If volatile (the default), the shared memory is automatically destroyed when no longer in use by any processes.

To retrieve an existing shared memory object, call:

```
shm = SharedMemory(id; readonly=false)
```

where `id` is the shared memory identifier (a string, an IPC key, or a System V IPC identifier of shared memory segment as returned by [`ShmId`](@ref)). Keyword `readonly` can be set true if only read access is needed. Note that method `shmid(obj)` may be called to retrieve the identifier of the shared memory object `obj`.

A number of accessors are available for a shared memory objects `shm`:

```
pointer(shm)    # base address of the shared memory
sizeof(shm)     # number of bytes of the shared memory
shmid(shm)      # identifier of the shared memory
```

To ensure that shared memory object `shm` is eventually destroyed, call:

```
rm(shm)
```

See also [`ShmId`](@ref), [`shmid`](@ref), and [`shmrm`](@ref).
