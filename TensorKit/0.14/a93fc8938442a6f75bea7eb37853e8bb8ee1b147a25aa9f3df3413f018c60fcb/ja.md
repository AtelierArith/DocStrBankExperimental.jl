```
rand([rng=default_rng()], [T=Float64], codomain::ProductSpace{S,N₁},
             domain::ProductSpace{S,N₂}) where {S,N₁,N₂,T} -> t
rand([rng=default_rng()], [T=Float64], codomain ← domain) -> t
```

`rand`によって生成されたエントリを持つテンソル`t`を生成します。

詳細は[`Random.rand!`](@ref)を参照してください。
