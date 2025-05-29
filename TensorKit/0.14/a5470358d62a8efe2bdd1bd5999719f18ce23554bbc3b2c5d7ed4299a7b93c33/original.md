```
hassector(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Bool
```

Query whether `P` has a non-zero degeneracy of sector `s`, representing a combination of sectors on the individual tensor indices.
