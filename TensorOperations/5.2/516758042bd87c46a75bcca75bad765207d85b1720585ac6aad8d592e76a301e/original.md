```
tensortrace!(C, A, p, q, conjA, α=1, β=0 [, backend, allocator])
```

Compute `C = β * C + α * permutedims(opA(A), (p, q))`, where `A` is partially traced, such that indices in `q[1]` are contracted with indices in `q[2]`, and the other indices are permuted according to `p`. The operation `opA` acts as `identity` if `conjA` equals `false` and as `conj` if `conjA` equals `true`. Optionally specify a backend implementation to use, and an allocator to be used if temporary tensor objects are needed.

!!! warning
    The object `C` must not be aliased with `A`.


See also [`tensortrace`](@ref).
