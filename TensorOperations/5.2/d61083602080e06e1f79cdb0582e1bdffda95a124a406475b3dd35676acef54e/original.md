```
tensortrace([IC], A, IA, [conjA], [α=1]; [backend=..., allocator=...])
tensortrace(A, p::Index2Tuple, q::Index2Tuple, conjA, α=1, [backend, allocator]) # expert mode
```

Trace or contract pairs of indices of tensor `A`, by assigning them identical indices in the iterable `IA`. The untraced indices, which are assigned a unique index, can be reordered according to the optional argument `IC`. The default value corresponds to the order in which they appear. Note that only pairs of indices can be contracted, so that every index in `IA` can appear only once (for an untraced index) or twice (for an index in a contracted pair).

Optionally, the symbol `conjA` can be used to specify that the input tensor should be conjugated.

See also [`tensortrace!`](@ref).
