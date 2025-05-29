```
dynamic_cufunction(f, tt=Tuple{})
```

Low-level interface to compile a function invocation for the currently-active GPU, returning a callable kernel object. Device-side equivalent of [`CUDA.cufunction`](@ref).

No keyword arguments are supported.
