```
alloc(h::HeapFunction, size::Integer; initialized::Bool=false) do size
    ptr = ...
end
```

Mark a block of code as allocating memory. The block should return a pointer to the allocated memory. The `initialized` argument indicates whether the memory is initialized or not.
