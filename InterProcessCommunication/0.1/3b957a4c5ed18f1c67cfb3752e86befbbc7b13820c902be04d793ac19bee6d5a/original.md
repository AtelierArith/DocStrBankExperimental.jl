## Named Semaphores

```julia
Semaphore(name, value; perms=0o600, volatile=true) -> sem
```

creates a new named semaphore identified by the string `name` of the form `"/somename"` and initial value set to `value`. An instance of `Semaphore{String}` is returned. Keyword `perms` can be used to specify access permissions. Keyword `volatile` specifies whether the semaphore should be unlinked when the returned object is finalized.

```julia
Semaphore(name) -> sem
```

opens an existing named semaphore and returns an instance of `Semaphore{String}`.

To unlink (remove) a persistent named semaphore, simply do:

```julia
rm(Semaphore, name)
```

If the semaphore does not exists, the error is ignored.  A `SystemError` is however thrown for other errors.

For maximum flexibility, an instance of a named semaphore may also be created by:

```julia
open(Semaphore, name, flags, mode, value, volatile) -> sem
```

where `flags` may have the bits `IPC.O_CREAT` and `IPC.O_EXCL` set, `mode` specifies the granted access permissions, `value` is the initial semaphore value and `volatile` is a boolean indicating whether the semaphore should be unlinked when the returned object `sem` is finalized. The values of `mode` and `value` are ignored if an existing named semaphore is open. The permissions settings in `mode` are masked against the process `umask`.

## Anonymous Semaphores

Anonymous semaphores are backed by *memory* objects providing the necessary storage.

```julia
Semaphore(mem, value; offset=0, volatile=true) -> sem
```

initializes an anonymous semaphore backed by memory object `mem` with initial value set to `value` and returns an instance of `Semaphore{typeof(mem)}`. Keyword `offset` can be used to specify the address (in bytes) of the semaphore data relative to `pointer(mem)`. Keyword `volatile` specify whether the semaphore should be destroyed when the returned object is finalized.

```julia
Semaphore(mem; offset=0) -> sem
```

yields an an instance of `Semaphore{typeof(mem)}` associated with an initialized anonymous semaphore and backed by memory object `mem` at relative position (in bytes) specified by keyword `offset`.

The number of bytes needed to store an anonymous semaphore is given by `sizeof(Semaphore)` and anonymous semaphore must be aligned in memory at multiples of the word size (that is `Sys.WORD_SIZE >> 3` in bytes). Memory objects used to store an anonymous semaphore must implement two methods: `pointer(mem)` and `sizeof(mem)` to yield respectively the base address and the size (in bytes) of the associated memory.

See also: [`post`](@ref), [`wait`](@ref), [`timedwait`](@ref),           [`trywait`](@ref).
