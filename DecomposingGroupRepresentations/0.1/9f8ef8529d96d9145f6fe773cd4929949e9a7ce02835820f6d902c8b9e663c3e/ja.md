```
GroupRepresentation <: AbstractGroupRepresentation
```

グループ表現を表します。グループ作用とベクトル空間から構成されています。

# コンストラクタ

```julia
GroupRepresentation(a::AbstractGroupAction, V::AbstractSpace)
```

# 例

```jldoctest
julia> @polyvar x[1:3];

julia> SO3 = LieGroup("SO", 3);

julia> a = MatrixGroupAction(SO3, [x]);

julia> V = FixedDegreePolynomials(x, 2);

julia> ρ = GroupRepresentation(a, V)
GroupRepresentation of SO(3) on 6-dimensional vector space
 Lie group: SO(3)

julia> dim(ρ)
6

julia> group(ρ)
LieGroup SO(3)
 number type (or field): ComplexF64
 weight type: Int64
 Lie algebra properties:
  dimension: 3
  rank (dimension of Cartan subalgebra): 1
```
