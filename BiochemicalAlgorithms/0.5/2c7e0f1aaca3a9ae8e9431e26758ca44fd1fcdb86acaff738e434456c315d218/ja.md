```
residues(::Chain)
residues(::ChainTable)
residues(::SecondaryStructure)
residues(::SecondaryStructureTable)
residues(::Molecule)
residues(::MoleculeTable)
residues(::System = default_system())
```

指定された原子コンテナまたはテーブルのすべての [`FragmentVariant.Residue`](@ref FragmentVariant) フラグメントを含む `FragmentTable{T}` を返します。

# サポートされているキーワード引数

[`fragments`](@ref) を参照してください。
