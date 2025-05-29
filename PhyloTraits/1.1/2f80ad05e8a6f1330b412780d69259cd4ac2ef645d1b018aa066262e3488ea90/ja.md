```
rand([rng::AbstractRNG,]
      model::TraitSubstitutionModel,
      t::Float64,
      start::AbstractVector{Int})
```

長さ t のエッジに沿った離散的な特性をシミュレートします。乱数生成器 `rng` はオプションです。`start` は整数のベクトルでなければならず、それぞれが1つの特性の開始値を表します。

# 例

```jldoctest
julia> m1 = BinaryTraitSubstitutionModel(1.0, 2.0)
Binary Trait Substitution Model:
rate 0→1 α=1.0
rate 1→0 β=2.0

julia> using StableRNGs; rng = StableRNG(135);

julia> rand(rng, m1, 0.2, [1,2,1,2,1])
5-element Vector{Int64}:
 2
 2
 1
 2
 1
```
