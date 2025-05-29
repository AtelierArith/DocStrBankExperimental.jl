```
randisometry([rng=default_rng()], [T=Float64], codomain::ProductSpace{S,N₁},
             domain::ProductSpace{S,N₂}) where {S,N₁,N₂,T} -> t
randisometry([rng=default_rng()], [T=Float64], codomain ← domain) -> t
```

`randisometry`を使用して生成されたエントリを持つテンソル`t`を生成します。

詳細は[`Random.randisometry!`](@ref)を参照してください。
