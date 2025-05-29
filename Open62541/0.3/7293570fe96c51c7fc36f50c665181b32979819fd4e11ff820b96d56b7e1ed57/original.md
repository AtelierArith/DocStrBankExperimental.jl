```
UInt16_clear(x::Ptr{UInt16})
```

deletes the dynamically allocated content of the object `x` and calls `UInt16_init(x)` to reset the type and its memory. 
