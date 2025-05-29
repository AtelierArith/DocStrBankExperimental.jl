```
@device_code_native [io::IO=stdout, ...] ex
```

Evaluates the expression `ex` and prints the result of [`GPUCompiler.code_native`](@ref) to `io` for every compiled GPU kernel. For other supported keywords, see [`GPUCompiler.code_native`](@ref).
