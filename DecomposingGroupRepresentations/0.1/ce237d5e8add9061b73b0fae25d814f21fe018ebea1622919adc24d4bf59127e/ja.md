```
IsotypicComponent <: AbstractGroupRepresentation
```

群表現の同型成分を表します。すなわち、同型の不可約表現の直和です。

# 例

```jldoctest
julia> @polyvar x[1:3] y[1:3];

julia> SO3 = LieGroup("SO", 3);

julia> a₁ = MatrixGroupAction(SO3, [x, y]);

julia> a₂ = ScalingLieGroupAction(vcat(x, y));

julia> a = a₁ × a₂;

julia> V = FixedDegreePolynomials(vcat(x, y), 2);

julia> ρ = GroupRepresentation(a, V)
GroupRepresentation of SO(3) × ℂˣ on 21-dimensional vector space
 Lie group: SO(3) × ℂˣ

julia> iso_decomp = isotypics(ρ)
IsotypicDecomposition of SO(3) × ℂˣ-action on 21-dimensional vector space
 同型成分の数: 3
 不可約表現の重複度: 3, 3, 1
 不可約表現の次元: 1, 5, 3
 同型成分の次元: 3, 15, 3

julia> iso = isotypics(iso_decomp)
3-element Vector{IsotypicComponent}:
 IsotypicComponent with (dim, mul) = (3, 3)
 IsotypicComponent with (dim, mul) = (15, 3)
 IsotypicComponent with (dim, mul) = (3, 1)

julia> iso[1]
IsotypicComponent of dimension 3, multiplicity 3
 Lie group: SO(3) × ℂˣ
 最高重み: [0, 2]
 不可約部分表現の次元: 1
 不可約部分表現の重複度: 3

julia> space(iso[1])
DirectSum of dimension 3
 summandsの数: 3
 summandsの次元: 1, 1, 1

julia> basis(iso[1])
3-element Vector{Polynomial{Commutative{CreationOrder}, Graded{LexOrder}, ComplexF64}}:
 x₃² + x₂² + x₁²
 y₃² + y₂² + y₁²
 -x₃y₃ + -x₂y₂ + -x₁y₁
```
