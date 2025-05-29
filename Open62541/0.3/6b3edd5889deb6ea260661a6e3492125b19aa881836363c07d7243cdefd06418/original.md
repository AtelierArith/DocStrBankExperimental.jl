```
UInt64_clear(x::Ptr{UInt64})
```

deletes the dynamically allocated content of the object `x` and calls `UInt64_init(x)` to reset the type and its memory. 
