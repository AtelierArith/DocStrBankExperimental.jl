```
PtrOrCuPtr{T}
```

A special pointer type, ABI-compatible with both `Ptr` and `CuPtr`, for use in `ccall` expressions to convert values to either a GPU or a CPU type (in that order). This is required for CUDA APIs which accept pointers that either point to host or device memory.
