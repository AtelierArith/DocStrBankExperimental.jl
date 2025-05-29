```
Buffer{T}
```

Buffer object to store data of type `T` with an offset.

The buffer allocates an extra element at the beginning which is used to check  if the buffer can be extended and to ensure that pointers to the allocated  arrays will never point to the same memory as the buffer.

If the buffer is used with [`reshape_buf!`](@ref), the offset is set to zero.
