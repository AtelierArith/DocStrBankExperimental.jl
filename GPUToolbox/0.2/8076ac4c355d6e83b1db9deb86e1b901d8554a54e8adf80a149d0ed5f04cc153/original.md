```
@gcsafe_ccall ...
```

Call a foreign function just like [`@ccall`](https://docs.julialang.org/en/v1/base/c/#Base.@ccall), but marking it safe for the GC to run. This is useful for functions that may block, so that the GC isn't blocked from running, but may also be required to prevent deadlocks (see JuliaGPU/CUDA.jl#2261).

Note that this is generally only safe with non-Julia C functions that do not call back into the Julia directly.
