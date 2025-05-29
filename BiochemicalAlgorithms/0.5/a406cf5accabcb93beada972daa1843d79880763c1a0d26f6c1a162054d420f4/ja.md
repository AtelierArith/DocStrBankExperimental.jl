```
parent_protein(::Atom)
parent_protein(::Chain)
parent_protein(::Fragment)
```

与えられたオブジェクトを含む `Molecule{T}` を返します。該当する分子が存在しない場合や、分子が [`MoleculeVariant.Protein`](@ref MoleculeVariant) でない場合は `nothing` を返します。
