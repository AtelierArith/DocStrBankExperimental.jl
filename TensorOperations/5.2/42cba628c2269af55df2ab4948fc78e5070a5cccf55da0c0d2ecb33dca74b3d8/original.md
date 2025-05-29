```
tensorcontract([IC], A, IA, [conjA], B, IB, [conjB], [α=1]; [backend=..., allocator=...])
tensorcontract(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, [backend, allocator]) # expert mode
```

Contract indices of tensor `A` with corresponding indices in tensor `B` by assigning them identical labels in the iterables `IA` and `IB`. The indices of the resulting tensor correspond to the indices that only appear in either `IA` or `IB` and can be ordered by specifying the optional argument `IC`. The default is to have all open indices of `A` followed by all open indices of `B`. Note that inner contractions of an array should be handled first with `tensortrace`, so that every label can appear only once in `IA` or `IB` seperately, and once (for an open index) or twice (for a contracted index) in the union of `IA` and `IB`.

Optionally, the symbols `conjA` and `conjB` can be used to specify that the input tensors should be conjugated.

See also [`tensorcontract!`](@ref).
