```
@cuda [kwargs...] func(args...)
```

High-level interface for executing code on a GPU. The `@cuda` macro should prefix a call, with `func` a callable function or object that should return nothing. It will be compiled to a CUDA function upon first use, and to a certain extent arguments will be converted and managed automatically using `cudaconvert`. Finally, a call to `cudacall` is performed, scheduling a kernel launch on the current CUDA context.

Several keyword arguments are supported that influence the behavior of `@cuda`.

  * `launch`: whether to launch this kernel, defaults to `true`. If `false` the returned kernel object should be launched by calling it and passing arguments again.
  * `dynamic`: use dynamic parallelism to launch device-side kernels, defaults to `false`.
  * arguments that influence kernel compilation: see [`cufunction`](@ref) and [`dynamic_cufunction`](@ref)
  * arguments that influence kernel launch: see [`CUDA.HostKernel`](@ref) and [`CUDA.DeviceKernel`](@ref)
