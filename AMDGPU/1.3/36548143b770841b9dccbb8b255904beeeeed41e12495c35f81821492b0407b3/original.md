```
@roc [kwargs...] func(args...)
```

High-level interface for launching kernels on GPU. Upon a first call it will be compiled, subsequent calls will re-use the compiled object.

Several keyword arguments are supported:

  * `launch::Bool = true`: whether to launch the kernel.   If `false`, then returns a compiled kernel which can be launched by   calling it and passing arguments.
  * Arguments that influence kernel compilation, see   [`AMDGPU.Compiler.hipfunction`](@ref).
  * Arguments that influence kernel launch, see [`AMDGPU.Runtime.HIPKernel`](@ref).
