```
MAllocBuffer{T}
```

Buffer object to store data of type `T` with an offset. The buffer memory is manually allocated and deallocated and is not extendable.

The buffer allocates an extra element at the beginning which is used to check  if the buffer can be extended and to ensure that pointers to the allocated  arrays will never point to the same memory as the buffer.

If the buffer is used with [`reshape_buf!`](@ref), the offset is set to zero.

!!! warning
    The memory is allocated manually, therefore the buffer must be freed manually as well.


!!! tip
    The buffer is intended to be used with [`@buffer`](@ref) macro, which frees the buffer after use.


# Example

```julia
julia> @buffer buf(100) begin
         A = alloc!(buf, 10, 10)
         B = alloc!(buf, 10, 10)
         C = alloc!(buf, 10, 10)
         A .= 1.0
         B .= 2.0
         @tensor C[i,j] = A[i,l] * B[l,j]
       end
```
