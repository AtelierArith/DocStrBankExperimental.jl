```
Int8_clear(x::Ptr{Int8})
```

deletes the dynamically allocated content of the object `x` and calls `Int8_init(x)` to reset the type and its memory. 
