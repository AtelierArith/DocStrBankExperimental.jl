```
tensoradd!(C, A, pA, conjA, α=1, β=1 [, backend, allocator])
```

Compute `C = β * C + α * permutedims(opA(A), pA)`. The operation `opA` acts as `identity` if `conjA` equals `:N` and as `conj` if `conjA` equals `:C`. Optionally specify a backend implementation to use, and an allocator to be used if temporary tensor objects are needed.

!!! warning
    The permutation needs to be trivial or `C` must not be aliased with `A`.


See also [`tensoradd`](@ref).
