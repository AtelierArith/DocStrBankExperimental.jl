```
sectors(P::ProductSpace{S, N}) where {S<:ElementarySpace}
```

Return an iterator over all possible combinations of sectors (represented as an `NTuple{N, sectortype(S)}`) that can appear within the tensor product space `P`.
