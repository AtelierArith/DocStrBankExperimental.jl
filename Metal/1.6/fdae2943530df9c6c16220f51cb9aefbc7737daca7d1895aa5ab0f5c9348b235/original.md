```
MtlDeviceArray(dims, ptr)
MtlDeviceArray{T}(dims, ptr)
MtlDeviceArray{T,A}(dims, ptr)
MtlDeviceArray{T,A,N}(dims, ptr)
```

Construct an `N`-dimensional dense Metal device array with element type `T` wrapping a pointer, where `N` is determined from the length of `dims` and `T` is determined from the type of `ptr`.

`dims` may be a single scalar, or a tuple of integers corresponding to the lengths in each dimension). If the rank `N` is supplied explicitly as in `Array{T,N}(dims)`, then it must match the length of `dims`. The same applies to the element type `T`, which should match the type of the pointer `ptr`.
