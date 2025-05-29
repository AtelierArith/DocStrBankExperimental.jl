```
MutableUniformArray(val, args...) -> A
MutableUniformArray{T}(val, args...) -> A
MutableUniformArray{T,N}(val, args...) -> A
```

build a mutable array `A` whose elements are initially all equal to `val` and whose axes are specified by `args...`. The difference with an instance of [`UniformArray`](@ref) is that the uniform value can be changed.

A statement like `A[i] = x` is allowed to change the value of all the elements of `A`; hence `i` must represent all indices of `A`. Call [`UniformArray(val, dims)`](@ref) to create an immutable uniform array whose element value cannot be changed.
