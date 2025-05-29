```
μₑᵤ, μₚᵤ, μₚₑ, αinv, αG, ΩΛ
```

物理的に測定された無次元の `Coupling` 値と不確かさは、電子と陽子の質量比 `μₑᵤ`、陽子と原子質量比 `μₚᵤ`、陽子と電子の質量比 `μₚₑ`、逆微細構造定数 `αinv`、および重力結合定数 `αG` です。

```Julia
julia> μₑᵤ # electronunit(Universe)
0.0005485799090649074

julia> μₚᵤ # protonunit(Universe)
1.007276466621

julia> μₚₑ # protonelectron(Universe)
1836.152673432705

julia> αinv # 1/finestructure(Universe)
137.035999084

julia> αG # coupling(Universe)
1.751809945750515e-45

julia> ΩΛ # darkenergydensity(Universe)
0.6889
```
