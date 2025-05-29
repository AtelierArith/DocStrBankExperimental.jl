```
UInt32_deleteMembers(x::Ptr{UInt32})
```

(deprecated, use `UInt32_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `UInt32_init(x)` to reset the type and its memory.
