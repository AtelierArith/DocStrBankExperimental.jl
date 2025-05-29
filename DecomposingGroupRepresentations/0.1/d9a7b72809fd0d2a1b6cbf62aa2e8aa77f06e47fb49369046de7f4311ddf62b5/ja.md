```
LieGroup{F} <: AbstractGroup{Lie, F}
```

行列リー群を表します。

# コンストラクタ

```julia
LieGroup(type::String, size::Int)
```

サポートされているリー群のタイプ: SO（特別直交）。

# 例

```jldoctest
julia> SO3 = LieGroup("SO", 3)
LieGroup SO(3)
 number type (or field): ComplexF64
 weight type: Int64
 Lie algebra properties:
  dimension: 3
  rank (dimension of Cartan subalgebra): 1
```
