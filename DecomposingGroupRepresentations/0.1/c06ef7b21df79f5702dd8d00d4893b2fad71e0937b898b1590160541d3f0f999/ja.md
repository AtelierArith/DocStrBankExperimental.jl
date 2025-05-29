```
ScalingLieGroup{F} <: AbstractGroup{Lie, F}
```

スケーリングリー群を表します。群の要素は対角行列です。

# コンストラクタ

```julia
ScalingLieGroup{F}(size::Int) where F
ScalingLieGroup{F}(exps::Matrix{Int}) where F
```

# 例

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
