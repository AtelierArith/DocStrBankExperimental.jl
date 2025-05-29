```
cudaconvert(x)
```

This function is called for every argument to be passed to a kernel, allowing it to be converted to a GPU-friendly format. By default, the function does nothing and returns the input object `x` as-is.

Do not add methods to this function, but instead extend the underlying Adapt.jl package and register methods for the the `CUDA.KernelAdaptor` type.
