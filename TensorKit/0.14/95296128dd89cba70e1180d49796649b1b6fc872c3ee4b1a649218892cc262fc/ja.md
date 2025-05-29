```
dim(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Int
```

与えられたテンソル積の各空間に対するセクターのタプルに対応する全体の縮退次元を返します。これは `prod(dims(P, s))` として得られます。
