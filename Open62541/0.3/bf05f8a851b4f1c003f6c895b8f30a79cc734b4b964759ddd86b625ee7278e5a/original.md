```
UInt64_deleteMembers(x::Ptr{UInt64})
```

(deprecated, use `UInt64_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `UInt64_init(x)` to reset the type and its memory.
