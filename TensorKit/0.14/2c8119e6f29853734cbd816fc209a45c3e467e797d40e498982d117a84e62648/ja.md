```
TensorMap{T}(undef, codomain::ProductSpace{S,N₁}, domain::ProductSpace{S,N₂})
            where {T,S,N₁,N₂}
TensorMap{T}(undef, codomain ← domain)
TensorMap{T}(undef, domain → codomain)
# expert mode: select storage type `A`
TensorMap{T,S,N₁,N₂,A}(undef, codomain ← domain)
TensorMap{T,S,N₁,N₂,A}(undef, domain → domain)
```

未初期化データを持つ `TensorMap` を構築します。
