```
dims(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Dims{N} = NTuple{N, Int}
```

テンソル積 `P` の各空間に対するセクターのタプル `s` に対応する縮退次元を返します。
