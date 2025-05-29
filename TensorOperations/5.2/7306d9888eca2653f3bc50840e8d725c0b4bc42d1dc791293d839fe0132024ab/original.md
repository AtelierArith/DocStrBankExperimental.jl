```
tensorcopy([IC=IA], A, IA, [conjA=false, [α=1]]; [backend=..., allocator=...])
tensorcopy(A, pA::Index2Tuple, conjA, α, [backend, allocator]) # expert mode
```

Create a copy of `A`, where the dimensions of `A` are assigned indices from the iterable `IA` and the indices of the copy are contained in `IC`. Both iterables should contain the same elements, optionally in a different order.

The result of this method is equivalent to `α * permutedims(A, pA)` where `pA` is the permutation such that `IC = IA[pA]`. The implementation of `tensorcopy` is however more efficient on average, especially if `Threads.nthreads() > 1`.

The optional argument `conjA` can be used to specify whether the input tensor should be conjugated (`true`) or not (`false`), whereas `α` can be used to scale the result. It is also optional to specify a backend implementation to use, and an allocator to be used if temporary tensor objects are needed.

See also [`tensorcopy!`](@ref).
