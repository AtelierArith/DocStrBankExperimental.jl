```
fuse(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
fuse(P::ProductSpace{S}) where {S<:ElementarySpace} -> S
```

個々の空間 `V₁`, `V₂`, ... の融合積または `P` に含まれる空間の融合積に同型の型 `S` の単一ベクトル空間を返します。
