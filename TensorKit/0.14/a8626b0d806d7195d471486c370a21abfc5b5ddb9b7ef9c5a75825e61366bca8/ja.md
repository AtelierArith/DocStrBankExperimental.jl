```
sectors(P::ProductSpace{S, N}) where {S<:ElementarySpace}
```

テンソル積空間 `P` 内に現れる可能性のあるすべてのセクターの組み合わせ（`NTuple{N, sectortype(S)}` として表される）を返すイテレータを返します。
