```
UInt8_clear(x::Ptr{UInt8})
```

deletes the dynamically allocated content of the object `x` and calls `UInt8_init(x)` to reset the type and its memory. 
