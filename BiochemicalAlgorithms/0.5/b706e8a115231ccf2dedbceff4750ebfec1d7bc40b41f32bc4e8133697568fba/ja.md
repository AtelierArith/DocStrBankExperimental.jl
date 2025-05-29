```
molecules(::System{T} = default_system())
```

指定されたシステムのすべての分子を含む `MoleculeTable{T}` を返します。

# サポートされているキーワード引数

  * `variant::Union{Nothing, MoleculeVariantType} = nothing`

キーワード引数は、結果を指定されたバリアントタイプに一致する分子に制限します。 `nothing` に設定されたキーワード引数は無視されます。
