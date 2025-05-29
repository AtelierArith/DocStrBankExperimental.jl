```
Float64_deleteMembers(x::Ptr{Float64})
```

(deprecated, use `Float64_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Float64_init(x)` to reset the type and its memory.
