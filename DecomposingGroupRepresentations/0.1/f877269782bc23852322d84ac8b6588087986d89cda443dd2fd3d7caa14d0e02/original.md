```
DirectProductGroup{T<:GroupType, F} <: AbstractDirectProductGroup{T, F}
```

Represents a direct product of groups.

# Examples

```jldoctest
julia> SO3 = LieGroup("SO", 3);

julia> T = ScalingLieGroup{ComplexF64}([1 2 3 4; -1 -2 -3 -4]);

julia> SO3 × SO3 × T
DirectProductGroup SO(3) × SO(3) × (ℂˣ)²
 number type (or field): ComplexF64
 3 factors: SO(3), SO(3), (ℂˣ)²
 Lie algebra:
  SumLieAlgebra 𝖘𝖔(3) ⊕ 𝖘𝖔(3) ⊕ ℂ²
  dimension: 8
  rank (dimension of Cartan subalgebra): 4
```
