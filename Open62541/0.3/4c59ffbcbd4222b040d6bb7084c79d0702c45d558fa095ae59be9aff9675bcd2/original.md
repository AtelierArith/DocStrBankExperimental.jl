```
Int32_clear(x::Ptr{Int32})
```

deletes the dynamically allocated content of the object `x` and calls `Int32_init(x)` to reset the type and its memory. 
