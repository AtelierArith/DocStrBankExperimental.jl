```
CuPtr{T}
```

A memory address that refers to data of type `T` that is accessible from the GPU. A `CuPtr` is ABI compatible with regular `Ptr` objects, e.g. it can be used to `ccall` a function that expects a `Ptr` to GPU memory, but it prevents erroneous conversions between the two.
