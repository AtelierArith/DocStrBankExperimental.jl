```
DirectProductGroup{T<:GroupType, F} <: AbstractDirectProductGroup{T, F}
```

群の直積を表します。

# 例

```jldoctest
julia> SO3 = LieGroup("SO", 3);

julia> T = ScalingLieGroup{ComplexF64}([1 2 3 4; -1 -2 -3 -4]);

julia> SO3 × SO3 × T
DirectProductGroup SO(3) × SO(3) × (ℂˣ)²
 数値型 (またはフィールド): ComplexF64
 3 つの因子: SO(3), SO(3), (ℂˣ)²
 リー代数:
  SumLieAlgebra 𝖘𝖔(3) ⊕ 𝖘𝖔(3) ⊕ ℂ²
  次元: 8
  ランク (カルタン部分代数の次元): 4
```
