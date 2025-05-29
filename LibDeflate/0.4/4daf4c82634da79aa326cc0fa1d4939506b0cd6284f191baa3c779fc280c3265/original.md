```
ReadableMemory
```

Struct that wraps a pointer and a length. This struct is not garbage-collector aware, so must be used with `GC.@preserve`. This can be constructed from types that are pointer-readable, like integer arrays. To make custom types available as input for `LibDeflate`, add a constructor taking your custom type.

See also: [`WriteableMemory`](@ref)
