```
HighestWeightModule <: AbstractSpace
```

最高重みモジュールは、リー群表現の文脈において最高重みモジュールを表します。

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

julia> H = space(irr_decomp[1])
HighestWeightModule of dimension 1
 Lie group: SO(3)
 highest weight: [0]

julia> basis(H)
1-element Vector{Polynomial{Commutative{CreationOrder}, Graded{LexOrder}, ComplexF64}}:
 z² + y² + x²
```
