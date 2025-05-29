```
randn([rng=default_rng()], [T=Float64], codomain::ProductSpace{S,N₁},
             domain::ProductSpace{S,N₂}) where {S,N₁,N₂,T} -> t
randn([rng=default_rng()], [T=Float64], codomain ← domain) -> t
```

エントリが `randn` によって生成されたテンソル `t` を生成します。

詳細は [`Random.randn!`](@ref) を参照してください。
