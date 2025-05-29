```
realloc(h::HeapFunction, ptr::Ptr{Nothing}, new_size::Integer;
        initialized::Bool=false) do ptr, new_size
    new_ptr = ...
end
```

Mark a block of code as reallocating memory at `ptr` to `new_size`. The block should return a pointer to the new memory.
