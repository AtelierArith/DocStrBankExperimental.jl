```
IrreducibleRepresentation <: AbstractGroupRepresentation
```

不変群表現を表します。

# 例

```jldoctest
julia> @polyvar x y z;

julia> vars = [x, y, z];

julia> SO3 = LieGroup("SO", 3);

julia> a = MatrixGroupAction(SO3, [vars]);

julia> V = FixedDegreePolynomials(vars, 2);

julia> ρ = GroupRepresentation(a, V);

julia> irr_decomp = irreducibles(ρ)
IrreducibleDecomposition of SO(3)-action on 6-dimensional vector space
 number of irreducibles: 2
 dimensions of irreducibles: 1, 5

julia> irr_decomp[2]
IrreducibleRepresentation of dimension 5
 Lie group: SO(3)
 highest weight: [2]

julia> space(irr_decomp[2])
HighestWeightModule of dimension 5
 Lie group: SO(3)
 highest weight: [2]

julia> basis(space(irr_decomp[2]))
5-element Vector{Polynomial{Commutative{CreationOrder}, Graded{LexOrder}, ComplexF64}}:
 -y² + (0.0 + 2.0im)xy + x²
 (0.0 + 1.0im)yz + xz
 (2.0 + 0.0im)z² + -y² + -x²
 (0.0 + 1.0im)yz + -xz
 -y² + (-0.0 - 2.0im)xy + x²
```
