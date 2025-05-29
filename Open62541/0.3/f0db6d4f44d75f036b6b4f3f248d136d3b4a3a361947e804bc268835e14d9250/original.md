```
Int32_deleteMembers(x::Ptr{Int32})
```

(deprecated, use `Int32_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Int32_init(x)` to reset the type and its memory.
