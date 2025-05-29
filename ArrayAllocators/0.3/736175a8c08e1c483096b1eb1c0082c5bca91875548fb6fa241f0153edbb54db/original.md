```
MemAlign([alignment::Integer])
```

Allocate aligned memory. Alias for platform specific implementations.

`alignment` must be a power of 2.

On POSIX systems, `alignment` must be a multiple of `sizeof(Ptr)`. On Windows, `alignment` must be a multiple of 2^16.

If `alignment` is not specified, it will be set to `min_alignment(MemAlign)`.

`MemAlign` is a constant alias for one the following platform specific implementations.

  * POSIX (Linux and macOS): [`POSIX.PosixMemAlign`](@ref)
  * Windows: [`Windows.WinMemAlign`](@ref).
