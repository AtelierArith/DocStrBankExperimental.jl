```
IrreducibleDecomposition
```

群表現の分解を不可約表現のコレクションに表します。

# コンストラクタ

```julia
IrreducibleDecomposition(ρ::GroupRepresentation)
```

# 例

```jldoctest
julia> @polyvar x y z;

julia> vars = [x, y, z];

julia> SO3 = LieGroup("SO", 3);

julia> a = MatrixGroupAction(SO3, [vars]);

julia> V = FixedDegreePolynomials(vars, 2);

julia> ρ = GroupRepresentation(a, V);

julia> irreducibles(ρ)
IrreducibleDecomposition of SO(3)-action on 6-dimensional vector space
 number of irreducibles: 2
 dimensions of irreducibles: 1, 5
```
