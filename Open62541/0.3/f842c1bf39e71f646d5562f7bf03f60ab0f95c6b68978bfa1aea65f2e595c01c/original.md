```
UInt32_clear(x::Ptr{UInt32})
```

deletes the dynamically allocated content of the object `x` and calls `UInt32_init(x)` to reset the type and its memory. 
