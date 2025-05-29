```
@alloc_ptr(n::Integer) -> Ptr{Nothing}
```

This can be used inside a `@no_escape` block to allocate a pointer which can hold `n` bytes. The memory used to allocate this pointer will come from the buffer associated with the enclosing `@no_escape` block.

Do not allow any references to this pointer to escape the enclosing `@no_escape` block, and do not pass these pointers to concurrent tasks unless that task is guaranteed to terminate before the `@no_escape` block ends. Any pointer allocated in this way which is found outside of its parent `@no_escape` block has undefined contents, and writing to this pointer will have undefined behaviour.
