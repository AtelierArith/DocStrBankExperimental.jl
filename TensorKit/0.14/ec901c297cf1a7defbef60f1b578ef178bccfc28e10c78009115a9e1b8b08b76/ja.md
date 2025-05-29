```
TensorMap(data::AbstractDict{<:Sector,<:AbstractMatrix}, codomain::ProductSpace{S,N₁},
            domain::ProductSpace{S,N₂}) where {S<:ElementarySpace,N₁,N₂}
TensorMap(data, codomain ← domain)
TensorMap(data, domain → codomain)
```

ブロックデータを明示的に指定して `TensorMap` を構築します。

## 引数

  * `data::AbstractDict{<:Sector,<:AbstractMatrix}`: 各結合セクター `c` のブロックデータをサイズ `(blockdim(codomain, c), blockdim(domain, c))` の行列として含む辞書。
  * `codomain::ProductSpace{S,N₁}`: 型 `S<:ElementarySpace` の `N₁` 空間の `ProductSpace` としてのコドメイン。
  * `domain::ProductSpace{S,N₂}`: 型 `S<:ElementarySpace` の `N₂` 空間の `ProductSpace` としてのドメイン。

また、ドメインとコドメインは、`codomain ← domain` または `domain → codomain` の構文を使用して [`HomSpace`](@ref) を渡すことで指定できます。
