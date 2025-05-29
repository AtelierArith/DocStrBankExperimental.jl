```
abstract type AbstractThreadLocal{T} end
```

Abstract type for thread-local values of type `T`.

The value for the current thread is accessed via `getindex(::AbstractThreadLocal)` and `setindex(::AbstractThreadLocal, x).

To access both regular and thread-local values in a unified manner, use the function [`getlocalvalue`](@ref).

To get the all values across all threads, use the function [`getallvalues`](@ref).

Default implementation is [`ThreadLocal`](@ref).
