```
Float64_clear(x::Ptr{Float64})
```

deletes the dynamically allocated content of the object `x` and calls `Float64_init(x)` to reset the type and its memory. 
