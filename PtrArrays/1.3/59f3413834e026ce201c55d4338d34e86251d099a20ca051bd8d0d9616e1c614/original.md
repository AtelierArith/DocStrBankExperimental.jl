```
PtrArray(ptr::Ptr{T}, dims::Int...; check_dims=true) <: DenseArray{T}
```

Wrap a pointer in an `DenseArray` interface conformant `PtrArray` using the standard Julia memory order.

Validates that `dims` are non-negative and don't overflow when multiplied if `check_dims` is true. Weird things might happen if you set `check_dims=false` and use negative or overflowing `dims`.

!!! note
    The Julia garbage collector is not able to track `Ptr`s, so the user is responsible for ensuring that the memory pointed to by `ptr` through `ptr + prod(dims) - 1` remains allocated throughout the time that the `PtrArray` is used and that mutable objects stored in a `PtrArray` are prevented from garbage collection.


see also [`malloc`](@ref), [`free`](@ref)
