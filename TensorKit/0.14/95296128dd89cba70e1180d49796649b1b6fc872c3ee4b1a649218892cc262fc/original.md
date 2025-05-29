```
dim(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Int
```

Return the total degeneracy dimension corresponding to a tuple of sectors for each of the spaces in the tensor product, obtained as `prod(dims(P, s))``.
