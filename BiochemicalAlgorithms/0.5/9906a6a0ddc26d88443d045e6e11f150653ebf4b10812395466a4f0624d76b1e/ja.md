```
nresidues(::Chain)
nresidues(::SecondaryStructure)
nresidues(::Molecule)
nresidues(::System = default_system())
```

指定された原子コンテナ内の[`FragmentVariant.Residue`](@ref FragmentVariant)フラグメントの数を返します。

# サポートされているキーワード引数

[`fragments`](@ref)を参照してください。
