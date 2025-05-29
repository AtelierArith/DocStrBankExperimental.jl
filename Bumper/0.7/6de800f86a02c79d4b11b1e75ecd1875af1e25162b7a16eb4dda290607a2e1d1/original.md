```
@alloc(T, n::Int...) -> UnsafeArray{T, length(n)}
```

This can be used inside a `@no_escape` block to allocate a `UnsafeArray` whose dimensions are determined by `n`. The memory used to allocate this array will come from the buffer associated with the enclosing `@no_escape` block.

Do not allow any references to this array to escape the enclosing `@no_escape` block, and do not pass these arrays to concurrent tasks unless that task is guaranteed to terminate before the `@no_escape` block ends. Any array allocated in this way which is found outside of its parent `@no_escape` block has undefined contents, and writing to this pointer will have undefined behaviour.
