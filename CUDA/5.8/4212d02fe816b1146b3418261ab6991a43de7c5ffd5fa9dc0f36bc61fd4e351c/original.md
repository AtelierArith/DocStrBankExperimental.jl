```
@device_code_sass [io::IO=stdout, ...] ex
```

Evaluates the expression `ex` and prints the result of [`CUDA.code_sass`](@ref) to `io` for every executed CUDA kernel. For other supported keywords, see [`CUDA.code_sass`](@ref).
