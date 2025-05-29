```
fragments(::Chain)
fragments(::SecondaryStructure)
fragments(::Molecule)
fragments(::System = default_system())
```

指定された原子コンテナのすべてのフラグメントを含む `FragmentTable{T}` を返します。

# サポートされているキーワード引数

  * `variant::Union{Nothing, FragmentVariantType} = nothing`
  * `molecule_idx::MaybeInt = nothing`
  * `chain_idx::MaybeInt = nothing`
  * `secondary_structure_idx::MaybeInt = nothing`

すべてのキーワード引数は、指定されたIDまたはバリアントタイプに一致するフラグメントに結果を制限します。 `nothing` に設定されたキーワード引数は無視されます。
