```
CuStaticSharedArray(T::Type, dims) -> CuDeviceArray{T,N,AS.Shared}
```

Get an array of type `T` and dimensions `dims` (either an integer length or tuple shape) pointing to a statically-allocated piece of shared memory. The type should be statically inferable and the dimensions should be constant, or an error will be thrown and the generator function will be called dynamically.
