```
UInt8_deleteMembers(x::Ptr{UInt8})
```

(deprecated, use `UInt8_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `UInt8_init(x)` to reset the type and its memory.
