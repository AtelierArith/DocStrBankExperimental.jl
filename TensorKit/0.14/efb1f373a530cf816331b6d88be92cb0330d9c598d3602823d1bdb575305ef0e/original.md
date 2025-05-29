```
dims(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Dims{N} = NTuple{N, Int}
```

Return the degeneracy dimensions corresponding to a tuple of sectors `s` for each of the spaces in the tensor product `P`.
