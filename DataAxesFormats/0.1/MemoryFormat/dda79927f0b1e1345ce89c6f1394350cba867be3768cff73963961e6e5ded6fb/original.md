```
struct MemoryDaf <: DafWriter ... end

MemoryDaf(; name = "memory")
```

Simple in-memory storage.

This just keeps everything in-memory, similarly to the way an `AnnData` object works; that is, this is a lightweight object that just keeps references to the data it is given.

This is the "default" storage type you should use, unless you need to persist the data on the disk.
