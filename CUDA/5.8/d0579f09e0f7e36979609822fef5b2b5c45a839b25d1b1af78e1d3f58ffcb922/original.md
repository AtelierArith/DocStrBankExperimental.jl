```
has_cuda_gpu()::Bool
```

Check whether the local system provides an installation of the CUDA driver and runtime, and if it contains a CUDA-capable GPU. See [`has_cuda`](@ref) for more details.

Note that this function initializes the CUDA API in order to check for the number of GPUs.
