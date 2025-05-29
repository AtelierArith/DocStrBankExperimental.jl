```
Float32_clear(x::Ptr{Float32})
```

deletes the dynamically allocated content of the object `x` and calls `Float32_init(x)` to reset the type and its memory. 
