```
Float32_deleteMembers(x::Ptr{Float32})
```

(deprecated, use `Float32_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Float32_init(x)` to reset the type and its memory.
