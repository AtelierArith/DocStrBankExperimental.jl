```
UniformArray(val, args...) -> A
UniformArray{T}(val, args...) -> A
UniformArray{T,N}(val, args...) -> A
```

build an immutable array `A` whose elements are all equal to `val` and whose axes are specified by `args...`. The storage requirement is `O(1)` instead of `O(length(A))` for an ordinary array `A`. Optional parameters `T` and `N` are to specify the element type and the number of dimensions of the array.

Uniform arrays implement conventional linear indexing: `A[i]` yields `val` for all linear indices `i` in the range `1:length(A)`.

A statement like `A[i] = x` is not implemented as uniform arrays are considered as immutable. Call [`MutableUniformArray(val, dims)`](@ref) to create a mutable uniform array.
