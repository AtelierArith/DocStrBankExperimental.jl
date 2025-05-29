```
tensorcontract!(C, A, pA, conjA, B, pB, conjB, pAB, α=1, β=0 [, backend, allocator])
```

Compute `C = β * C + α * permutedims(contract(opA(A), opB(B)), pAB)` without creating the intermediate temporary, where `A` and `B` are contracted such that the indices `pA[2]` of `A` are contracted with indices `pB[1]` of `B`. The remaining indices `(pA[1]..., pB[2]...)` are then permuted according to `pAB`. The operation `opA` acts as `identity` if `conjA` equals `false` and as `conj` if `conjA` equals `true`; the operation `opB` is determined by `conjB` analogously. Optionally specify a backend implementation to use, and an allocator to be used if temporary tensor objects are needed.

!!! warning
    The object `C` must not be aliased with `A` or `B`.


See also [`tensorcontract`](@ref).
