```
Bool_deleteMembers(x::Ptr{Bool})
```

(deprecated, use `Bool_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Bool_init(x)` to reset the type and its memory.
