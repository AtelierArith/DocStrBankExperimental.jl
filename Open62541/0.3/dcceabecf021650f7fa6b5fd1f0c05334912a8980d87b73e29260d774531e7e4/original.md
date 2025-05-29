```
UInt16_deleteMembers(x::Ptr{UInt16})
```

(deprecated, use `UInt16_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `UInt16_init(x)` to reset the type and its memory.
