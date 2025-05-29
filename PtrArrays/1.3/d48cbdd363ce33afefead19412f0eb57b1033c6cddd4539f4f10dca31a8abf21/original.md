```
malloc(T::Type, dims::Int...) -> PtrArray{T, N} <: AbstractArray{T, N}
```

Allocate a new array of type `T` and dimensions `dims` using the C stdlib's `malloc`.

`T` must be an `isbitstype`.

This array is not tracked by Julia's garbage collector, so it is the user's responsibility to call [`free`](@ref) on it when it is no longer needed.
