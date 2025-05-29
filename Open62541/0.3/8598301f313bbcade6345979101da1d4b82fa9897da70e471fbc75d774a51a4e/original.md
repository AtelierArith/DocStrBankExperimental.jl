```
Int64_deleteMembers(x::Ptr{Int64})
```

(deprecated, use `Int64_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Int64_init(x)` to reset the type and its memory.
