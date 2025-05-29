```
IsotypicComponent <: AbstractGroupRepresentation
```

Represents an isotypic component of a group representation, i.e. a direct sum of isomorphic irreducible representations.

# Examples

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
 number of isotypic components: 3
 multiplicities of irreducibles: 3, 3, 1
 dimensions of irreducibles: 1, 5, 3
 dimensions of isotypic components: 3, 15, 3

julia> iso = isotypics(iso_decomp)
3-element Vector{IsotypicComponent}:
 IsotypicComponent with (dim, mul) = (3, 3)
 IsotypicComponent with (dim, mul) = (15, 3)
 IsotypicComponent with (dim, mul) = (3, 1)

julia> iso[1]
IsotypicComponent of dimension 3, multiplicity 3
 Lie group: SO(3) × ℂˣ
 highest weight: [0, 2]
 dimension of irreducible subrepresentation: 1
 multiplicity of irreducible subrepresentation: 3

julia> space(iso[1])
DirectSum of dimension 3
 nsummands: 3
 dimensions of summands: 1, 1, 1

julia> basis(iso[1])
3-element Vector{Polynomial{Commutative{CreationOrder}, Graded{LexOrder}, ComplexF64}}:
 x₃² + x₂² + x₁²
 y₃² + y₂² + y₁²
 -x₃y₃ + -x₂y₂ + -x₁y₁
```
