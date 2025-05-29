```
one(::S) where {S<:ElementarySpace} -> ProductSpace{S, 0}
one(::ProductSpace{S}) where {S<:ElementarySpace} -> ProductSpace{S, 0}
```

ゼロ空間のテンソル積を返します。これは型 `S` の単位オブジェクトであり、テンソル積演算の下で `V ⊗ one(V) == V` となります。
