```
Int16_deleteMembers(x::Ptr{Int16})
```

(deprecated, use `Int16_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Int16_init(x)` to reset the type and its memory.
