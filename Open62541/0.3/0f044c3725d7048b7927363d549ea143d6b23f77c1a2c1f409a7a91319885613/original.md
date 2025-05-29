```
Int64_clear(x::Ptr{Int64})
```

deletes the dynamically allocated content of the object `x` and calls `Int64_init(x)` to reset the type and its memory. 
