```
protein_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Molecule{T}
```

指定された `idx` に関連付けられた `Molecule{T}` を `sys` から返します。該当する分子が存在しない場合や、分子が [`MoleculeVariant.Protein`](@ref MoleculeVariant) でない場合は `KeyError` をスローします。
