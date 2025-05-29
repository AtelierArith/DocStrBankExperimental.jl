```
IsotypicDecomposition
```

群表現の同型分解を表します。

# コンストラクタ

```julia
IsotypicDecomposition(ρ::GroupRepresentation)
```

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

julia> isotypics(ρ)
IsotypicDecomposition of SO(3) × ℂˣ-action on 21-dimensional vector space
 number of isotypic components: 3
 multiplicities of irreducibles: 3, 3, 1
 dimensions of irreducibles: 1, 5, 3
 dimensions of isotypic components: 3, 15, 3
```
