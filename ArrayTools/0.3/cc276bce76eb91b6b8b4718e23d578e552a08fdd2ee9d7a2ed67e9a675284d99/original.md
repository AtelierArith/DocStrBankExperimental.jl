```
to_flat_array([T=eltype(A),] A)
```

lazily yields a *flat* array based on `A`, that is an array with contiguous elements in column-major order and first element at index 1. Optional argument `T` is to specify the element type of the result. Argument `A` is returned if it is already a flat array with the requested element type; otherwise, `convert` method is called to produce the result (an `Array{T}` in that case).

See also [`is_flat_array`](@ref), [`to_fast_array`](@ref).
