```
ScalingLieGroup{F} <: AbstractGroup{Lie, F}
```

Represents a scaling Lie group. The group elements are diagonal matrices.

# Constructors

```julia
ScalingLieGroup{F}(size::Int) where F
ScalingLieGroup{F}(exps::Matrix{Int}) where F
```

# Examples

```jldoctest
julia> ScalingLieGroup{ComplexF64}(5)
ScalingLieGroup ℂˣ
 number type (or field): ComplexF64
 Lie algebra properties:
  dimension: 1
  basis (diagonal matrices):
   [1, 1, 1, 1, 1]
```

```jldoctest
julia> exps = [1 1 1 0 0 0; 0 0 0 1 -2 0];

julia> ScalingLieGroup{ComplexF64}(exps)
ScalingLieGroup (ℂˣ)²
 number type (or field): ComplexF64
 Lie algebra properties:
  dimension: 2
  basis (diagonal matrices):
   [1, 1, 1, 0, 0, 0]
   [0, 0, 0, 1, -2, 0]
```
