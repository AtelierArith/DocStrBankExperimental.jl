```
hassector(P::ProductSpace{S, N}, s::NTuple{N, sectortype(S)}) where {S<:ElementarySpace}
-> Bool
```

`P`が個々のテンソルインデックス上のセクターの組み合わせを表すセクター`s`の非ゼロの縮退を持っているかどうかを照会します。
