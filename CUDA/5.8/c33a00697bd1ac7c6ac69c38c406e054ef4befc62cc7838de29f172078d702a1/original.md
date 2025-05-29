```
CuDynamicSharedArray(T::Type, dims, offset::Integer=0) -> CuDeviceArray{T,N,AS.Shared}
```

Get an array of type `T` and dimensions `dims` (either an integer length or tuple shape) pointing to a dynamically-allocated piece of shared memory. The type should be statically inferable or an error will be thrown and the generator function will be called dynamically.

Note that the amount of dynamic shared memory needs to specified when launching the kernel.

Optionally, an offset parameter indicating how many bytes to add to the base shared memory pointer can be specified. This is useful when dealing with a heterogeneous buffer of dynamic shared memory; in the case of a homogeneous multi-part buffer it is preferred to use `view`.
