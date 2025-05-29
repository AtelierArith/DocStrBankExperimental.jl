```
NLLSsolver.robustkernel(mycost)
```

Return a subtype of AbstractRobustifier with which to robustify `mycost`.

Existing kernels are [`NoRobust`](@ref), [`Scaled`](@ref), [`HuberKernel`](@ref) and [`GemanMcclureKernel`](@ref). You may also write your own.

!!! tip
    If your cost is a pure sum of squares (i.e. unrobustified), do not implement this method.


!!! note
    Optional user-specialized API function.

