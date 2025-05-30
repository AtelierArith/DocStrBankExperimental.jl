```
realloc(h::HeapFunction, ptr::Ptr{Nothing}, new_size::Integer;
        initialized::Bool=false) do ptr, new_size
    new_ptr = ...
end
```

`ptr`を`new_size`に再割り当てするコードブロックをマークします。このブロックは新しいメモリへのポインタを返す必要があります。
