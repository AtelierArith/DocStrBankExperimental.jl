```
tensorproduct([IC], A, IA, [conjA], B, IB, [conjB], [α=1]; [backend=..., allocator=...])
tensorproduct(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, [backend, allocator]) # expert mode
```

Compute the tensor product (outer product) of two tensors `A` and `B`, i.e. returns a new tensor `C` with `ndims(C) = ndims(A) + ndims(B)`. The indices of the output tensor are related to those of the input tensors by the pattern specified by the indices. Essentially, this is a special case of [`tensorcontract`](@ref) with no indices being contracted over. This method checks whether the indices indeed specify a tensor product instead of a genuine contraction.

Optionally, the symbols `conjA` and `conjB` can be used to specify that the input tensors should be conjugated.

See also [`tensorproduct!`](@ref) and [`tensorcontract`](@ref).
