```
Int8_deleteMembers(x::Ptr{Int8})
```

(deprecated, use `Int8_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Int8_init(x)` to reset the type and its memory.
