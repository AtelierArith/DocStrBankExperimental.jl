```
to_fast_array([T=eltype(A),] A)
```

lazily yields a *fast array* equivalent to `A` with element type `T`. A *fast array* has standard 1-based indices and is efficiently indexed by linear indices. If `A` is already a *fast array* with element type `T`, `A` is returned; otherwise, `A` is converted into an `Array` which is returned.

See also [`is_fast_array`](@ref), [`IndexingType`](@ref), [`to_flat_array`](@ref).
