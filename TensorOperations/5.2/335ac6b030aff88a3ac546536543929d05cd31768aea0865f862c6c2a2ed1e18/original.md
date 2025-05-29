```
tensoradd([IC=IA], A, IA, [conjA], B, IB, [conjB], [α=1, [β=1]]; [backend=..., allocator=...])
tensoradd(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, α=1, β=1, [backend, allocator]) # expert mode
```

Return the result of adding arrays `A` and `B` where the iterables `IA` and `IB` denote how the array data should be permuted in order to be added. More specifically, the result of this method is equivalent to `α * permutedims(A, pA) + β * permutedims(B, pB)` where `pA` (`pB`) is the permutation such that `IC = IA[pA]` (`IB[pB]`). The implementation of `tensoradd` is however more efficient on average, as the temporary permuted arrays are not created.

Optionally, the symbols `conjA` and `conjB` can be used to specify whether the input tensors should be conjugated (`true`) or not (`false`).

See also [`tensoradd!`](@ref).
