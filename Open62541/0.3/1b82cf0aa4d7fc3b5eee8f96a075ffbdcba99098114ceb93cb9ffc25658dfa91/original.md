```
Bool_clear(x::Ptr{Bool})
```

deletes the dynamically allocated content of the object `x` and calls `Bool_init(x)` to reset the type and its memory. 
