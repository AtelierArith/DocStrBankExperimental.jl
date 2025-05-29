```
nucleotides(::Chain)
nucleotides(::ChainTable)
nucleotides(::SecondaryStructure)
nucleotides(::SecondaryStructureTable)
nucleotides(::Molecule)
nucleotides(::MoleculeTable)
nucleotides(::System = default_system())
```

指定された原子コンテナまたはテーブルのすべての [`FragmentVariant.Nucleotide`](@ref FragmentVariant) フラグメントを含む `FragmentTable{T}` を返します。

# サポートされているキーワード引数

[`fragments`](@ref) を参照してください。
