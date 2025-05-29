```
@device_code_llvm [io::IO=stdout, ...] ex
```

Evaluates the expression `ex` and prints the result of `InteractiveUtils.code_llvm` to `io` for every compiled GPU kernel. For other supported keywords, see [`GPUCompiler.code_llvm`](@ref).

See also: InteractiveUtils.@code_llvm
