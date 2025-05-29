```
internal_operation_mode(xs::Tuple)
internal_operation_mode(x::AbstractArray)
```

Returns the internal operation mode for the given array(s). This is useful to define custom implementations using different backends like simple Julia broadcasting, Kernel Abstractions, Loop Vectorization, etc.

Currently supported modes are:

  * `GenericBroadcastOp`: This is the fallback for most types. For the following types this is the preferred mode:

      * Arrays with `fast_scalar_indexing` set to `False`.
      * Static Arrays
      * ReverseDiff Arrays
      * Tracker Arrays
      * ForwardDiff.Dual Arrays
      * Complex Arrays
  * `GPUBroadcastOp{dev}`: GPU Arrays where `dev` is obtained from `get_device_type(xs)`. This option dispatches should preferably use `KernelAbstractions` or specialized vendor dispatches.
  * `LoopedArrayOp`: CPU arrays that can be optimized using SIMD Loops, ideally using `LoopVectorization.jl` or `Polyester.jl`.
