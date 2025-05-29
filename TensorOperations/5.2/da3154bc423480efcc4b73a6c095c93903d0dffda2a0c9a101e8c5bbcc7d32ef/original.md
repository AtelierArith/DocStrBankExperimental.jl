```
tensorproduct!(C, A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, β=0, [backend, allocator])
```

Compute the tensor product (outer product) of two tensors `A` and `B`, i.e. a wrapper of [`tensorcontract!`](@ref) with no indices being contracted over. This method checks whether the indices indeed specify a tensor product instead of a genuine contraction.  Optionally  specify a backend implementation to use, and an allocator to be used if temporary tensor objects are needed.

!!! warning
    The object `C` must not be aliased with `A` or `B`.


See als [`tensorproduct`](@ref) and [`tensorcontract!`](@ref).
